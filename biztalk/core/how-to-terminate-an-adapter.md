---
description: "Learn more about: How to Terminate an Adapter"
title: "How to Terminate an Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dfba2b61-b89f-41cd-a014-4e96daec6516
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Terminate an Adapter
The following topics provide guidance on the proper shutdown of an adapter.  
  
## Terminating an Adapter  
 When the Messaging Engine is shutting down it calls **IBTTransportControl**.**Terminate** on each in-process adapter. After this method returns BizTalk Server will destroy the adapter. For native adapters this occurs immediately, but for managed adapters exactly when this occurs is less deterministic due to the .NET garbage-collection process. The adapter should block in **Terminate** and do any necessary cleanup work until it is ready to be destroyed.  
  
## Terminating Isolated Receive Adapters  
 Isolated receive adapters do not have **Terminate** called on them because they are not hosted in the BizTalk service. Instead, they should call **IBTTransportProxy**.**TerminateIsolatedReceiver** to notify the Messaging Engine that they are about to shut down.  
  
## Clean Up COM Objects by Using Marshal.ReleaseComObject  
 When writing managed code that uses COM objects, the common language runtime (CLR) generates proxy objects that hold the references to the COM objects. The proxy objects are managed objects and are subject to the usual rules of garbage collection. A problem arises in that the garbage collector only sees memory that the .NET runtimes allocated, and is not aware of the COM object. Because the proxy objects are small, a large COM object might be left in memory because the CLR garbage collector is not aware of it.  
  
 To avoid this problem, explicitly release underlying COM objects when you are finished with them, particularly any **IBTTransportBatch** objects. You do this by calling **Marshal**.**ReleaseComObject**.  
  
> [!NOTE]
>  **ReleaseComObject** returns the number of remaining references and only releases the COM object when this returned value is zero. Often **ReleaseComObject** is called in a loop to ensure that the object is released. After that is complete, you should call **SuppressFinalize** on this object because there is nothing to finalize. One last step is to check whether this really is a COM object.  
  
 The following code shows the process descrjbed above:  
  
```  
if (Marshal.IsComObject (batch))  
(  
While (0 <Marshal.ReleaseComObject(batch)  
;  
GC.SuppressFinalize (batch);  
  
```  
  
 Explicitly releasing the **IBTTransportBatch** object returned from **GetBatch** can make a significant improvement to performance.  
  
## Always Use Terminate When Closing an Adapter  
 For BizTalk Server to recognize your code as an adapter, you must implement an interface called **IBTTransportControl**. This interface defines how BizTalk Server communicates with your adapter, and is defined as follows:  
  
```  
public interface IBTTransportControl   
{  
void Initialize(IBTTransportProxy transportProxy);  
void Terminate();  
}  
```  
  
 The interface contains two methods, **Initialize** and **Terminate**.  
  
### Initialize  
 BizTalk Server calls the **Initialize** method after it loads the adapter assembly. It does this to pass the transport proxy (the main handle to BizTalk Server) to the adapter. The implementation of **Initialize** simply stores the transport proxy in a member variable.  
  
### Terminate  
 BizTalk Server calls the **Terminate** method on service shutdown to give the adapter time to finish the execution of all batches. This makes the implementation of the **Terminate** method much more involved.  
  
 The adapter should not return from a **Terminate** call until any pending work it has is complete. When BizTalk Server calls **Terminate**, the adapter should try to stop all its current tasks and not start any new ones.  
  
 Because **Terminate** is called as part of the service shutdown, the service control manager ends the process if the adapter perpetually blocks in **Terminate**. In this case, you see the warning from the service control manager as it stops the BizTalk Server service. If possible, avoid terminating the adapter prematurely like this. If the adapter does not handle the termination process appropriately, and still has threads running when the process starts to shut down, then you may occasionally see an access violation from BizTalk Server on shutdown.  
  
 Because of the asynchronous nature of the interface to BizTalk Server, it is likely that under load there will be many batches and therefore threads still being executed. The **Terminate** call should be implemented to wait on the conclusion of every batch the adapter has successfully executed on BizTalk Server before proceeding. The conclusion of the batch is signaled by the **BatchComplete** callback from BizTalk Server. The **Terminate** call should wait on every pending **BatchComplete** to happen. However, the execution of the batch must be successful. That is, the call to **IBTTransportBatch**::**Done** must not fail. If the call to **IBTTransportBatch**::**Done** fails, there is no batch callback.  
  
 After you realize that you have to add synchronization code to your adapter, the implementation is fairly straightforward.  
  
 One simple approach is to implement a compound synchronization object with **enter** and **leave** methods for the worker threads and a **terminate** method that blocks while a thread is still within the protected execution. (Incidentally, the solution is very similar to the familiar multiple-reader, single-writer structure where the worker threads can be thought of as readers and the **terminate** method as the writer.)  
  
 The **terminate** method is as follows:  
  
```  
void terminate ()  
{  
this.control.Terminate();  
}  
```  
  
 For each worker thread:  
  
```  
If (!this.control.Enter())  
return; // we can’t enter because Terminate has been called  
try  
{  
//  create and fill batch  
batch.Done();  
}  
catch (Exception)  
{  
//  we are not expecting a callback  
This.control.Leave();  
}  
```  
  
 In the callback from BizTalk Server:  
  
```  
batchComplete (…)  
{  
//  the callback from BizTalk Server  
//  process results  
this.control.Leave();  
}  
```  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ships with sample code ControlledTermination.cs in the Base Adapter sample, showing the synchronization mechanism described here.
