---
title: "Using the Ops Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IOpsAIC interface"
  - "Ops adapters, configuring"
  - "Ops adapters, IOpsAIC interface"
  - "process management solution tutorial, Ops adapters"
  - "Ops adapters, processing"
ms.assetid: 331f3614-e00b-4587-b82b-3c7bc394f361
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the Ops Adapter
The business process management solution uses the Ops adapter to handle error reports from the new error reporting feature. The solution includes a sample handler to process messages from the adapter, although you can easily write your own and use the adapter in other solutions. For information about the error reporting feature, see [Using Failed Message Routing](../core/using-failed-message-routing.md).  
  
> [!NOTE]
>  Although the solution uses the adapter for error reporting, its use is not limited to error handling. You can use the adapter in a variety of circumstances whenever you want to execute a specific object method in response to a message.  
  
## How the Ops Adapter Processes Error Reports  
 Ports in the solution that use error reporting ultimately send the error messages to the **BizTalkErrors-SP** port. The filter on the port tests for the existence of the **ErrorReport.ErrorType** context property. Only error report messages have this context property.  
  
 The **BizTalkErrors-SP** send port runs the error message through a pipeline that uses an XML assembler component to put the message in an envelope. The message then goes to the Ops adapter.  
  
 The envelope, defined by the ErrorEnvelope schema, is marked to accept any type of message. However, "any" means any message type defined in the BizTalk group. This can produce suspended messages if the solution receives a message of an unknown type. Such a message would produce an error and would be routed to the **BizTalkErrors-SP** port. In turn, the message would generate an error in the XML assembler component of the pipeline because it would not be a known message type. The pipeline error suspends the message.  
  
> [!NOTE]
>  To handle routing errors due to unknown message types, you must write a custom pipeline component and use the component in a custom pipeline for the **BizTalkErrors-SP** port. The custom component replaces the XML assembler component. Your custom component must put the **ErrorReport** properties in the envelope header and add the message to the body of the envelope.  
  
 The Ops adapter is a transactional, one-way send adapter. When the adapter processes a message, it first loads the specified assembly, if necessary. The adapter caches assemblies in memory to avoid the overhead of loading the assembly for each call. It then creates an instance of the specified class, and then uses reflection to get the object in the assembly implementing the **IOpsAIC** interface. If all of this is successful, the adapter calls the **Initialize** method and then calls the **Execute** method, passing the error report message.  
  
 If there is an error calling **Execute**, the adapter resubmits the message. If the specified class does not implement the **IOpsAIC** interface, or the class or assembly can't be found, the adapter suspends the message.  
  
> [!TIP]
>  Because the adapter uses reflection, the assembly containing the class must be in the Global Assembly Cache (GAC).  
  
## The IOpsAIC Interface  
 The adapter requires an object that implements the **IOpsAIC** interface. The interface appears as follows:  
  
```  
interface IOpsAIC  
{  
    void Initialize(string config);  
    void Execute(byte[] message);  
}  
```  
  
 The adapter passes the original message as a byte array to the **Execute** method.  
  
## Configuring the Adapter  
 You configure the adapter just as you would any other adapter. The following table describes the adapter's configuration properties:  
  
|Display Name|Description|  
|------------------|-----------------|  
|**.NET Assembly Strong Name**|The fully qualified name of the assembly.|  
|**OpsAIC Class Name**|The name of the class within the assembly that implements the **IOpsAIC** interface.|  
|**Initialization Data**|A string passed as an argument to the **Initialize** method of the class.|  
  
 Notice that the adapter requires the fully qualified name of the assembly. The fully qualified name is the name given to an assembly when you add it to the GAC. The fully qualified name is a string containing the assembly's name, version, culture, and public key token. You can see the fully qualified names of assemblies by using the Global Assembly Cache Tool, gacutil.exe.  
  
 For more information about fully qualified assembly names, see "Assembly Names" in the .NET Framework Developer's Guide. For more information about gacutil.exe, see "Global Assembly Cache Tool (Gacutil.exe)" in the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Developer's Guide.  
  
 You must provide the namespace with the class name. For example, if the class is **OpsHandler** in the **OperationsHandler** namespace, you would give the class name as **OperationsHandler.OpsHandler**.  
  
## See Also  
 [The Ops Adapter](../core/the-ops-adapter.md)