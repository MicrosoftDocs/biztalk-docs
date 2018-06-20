---
title: "Support for Queue Management | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d60d06ba-8cf3-46d6-af59-626f12fc572a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Support for Queue Management
With the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MQSeries adapter you can now create and delete queues remotely on the MQSeries Queue Manager. This is supported because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses a remote MQSAgent COM+ object that communicates directly with the MQSeries Queue Manager. Typically this MQSAgent is used at run time to read and write messages to the remote MQSeries Server queues. More than one BizTalk server can be a client of this remote service. Additionally, queue creation and deletion functions are provided by this MQSAgent and can be called directly from within an orchestration or adapter. This allows for highly dynamic scenarios whereby the orchestration or adapter can create a temporary queue and then send a message on it, receive a reply on another queue, and finally delete the temporary queue.  
  
## CreateQueue and DeleteQueue APIs  
 The CreateQueue and DeleteQueue APIs are defined as follows.  
  
### Structure Definition  
  
```  
typedef enum QueueUsage {  
      Normal       = 0,  
      Transmission = 1  
} QueueUsage;  
  
typedef enum ResultCode {  
      QueueAlreadyExists                     = 0, //  no bits set  
      QueueCreated                           = 1, //  QueueCreated  
      QueueCreatedAndRemoteDefinitionUpdated = 5, //  QueueCreated | RemoteDefinitionUpdated  
      QueueAndRemoteDefinitionCreated        = 7, //  QueueCreated | RemoteDefinitionCreated | RemoteDefinitionUpdated  
      QueueDoesNotExist                      = 8, //  QueueDoesNotExist  
      QueueDeleted                           = 16 //  QueueDeleted  
} ResultCode;  
```  
  
### Interface Definition  
  
```  
[  
            object,  
            uuid(E90AC1A6-657B-4680-AF6A-89F11113FB8B),  
            dual,  
            nonextensible,  
            helpstring("IMQSAdmin Interface"),  
            pointer_default(unique)  
]  
interface IMQSAdmin2 : IDispatch{  
  
HRESULT CreateQueue (  
[in]BSTR queueManager,  
[in]BSTR newQueueName,  
[in]QueueUsage usage,  
[in]BSTR remoteDefinition,  
[in]BSTR remoteQName,  
[in]BSTR remoteQMgrName,  
[in]BOOL updateExistingRemoteDefinition,  
[out, retval]ResultCode* resultCode);  
  
HRESULT DeleteQueue (  
[in]BSTR queueManager,  
[in]BSTR newQueueName,  
[out, retval]ResultCode* resultCode);  
};  
  
      [  
            uuid(412AF00D-7CA8-4d2a-AFF6-F61CE2E29A0D),  
            helpstring("MQSAdmin Class")  
      ]  
      coclass MQSAdmin  
      {  
            [default] interface IMQSAdmin2;  
      };  
  
```  
  
## Examples  
 Complete the steps in Example 1 to create a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] C# console application which can be used to create or delete MQSeries Server queues.  
  
### Example 1  
  
##### Create a C# console application to manage MQSeries Server queues  
  
1. Create a new Visual C# Console Application in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] with the name **MQSeriesQueues**.  
  
2. Replace any existing code in the Program.cs file that is generated with the code below:  
  
   ```  
   using System;  
   using System.Collections.Generic;  
   using System.Text;  
   using MQSAgentLib;  
  
   namespace MQSeriesQueues  
   {  
       class ManageQueues  
       {  
           public static void Main(string[] args)  
           {  
               // The first argument should be "c" (without quotes)  
               // to create a queue, anything else to delete a queue.  
               // The 2nd and 3rd arguments should be the name of   
               // the MQSeries Queue Manager and the name of   
               // the queue to be created or deleted for example  
               // the following usage will create the local   
               // queue testq for the Queue Manager QM_Test  
               // MQSeriesQueues c QM_Test testq  
               createordeleteQs(args[0], args[1], args[2]);  
           }  
  
           static void createordeleteQs(string Qswitch, string QMgr, string QName)  
           {   
           if ((Qswitch =="c" & (QMgr != null & QName != null)))  
               {  
                   CreateQueue(QMgr, QName);  
               }  
               else if(QMgr != null & QName != null)  
               {  
                   DeleteQueue(QMgr, QName);  
               }  
            }  
  
           static void CreateQueue(string Qmgr, string Qname)  
           {  
               MQSAdmin admin = new MQSAdmin();    
  
               ResultCode resultCode = admin.CreateQueue(Qmgr, Qname, 0, "", "", "", 0);  
  
               if ((resultCode & ResultCode.QueueCreated) == ResultCode.QueueCreated)  
               {  
                   Console.WriteLine("Queue Created.");  
               }  
               else if ((resultCode & ResultCode.QueueAlreadyExists) == ResultCode.QueueAlreadyExists)  
               {  
                   Console.WriteLine("Queue Already Exists.");  
               }  
           }  
  
           static void DeleteQueue(string Qmgr, string Qname)  
           {  
               MQSAdmin admin = new MQSAdmin();  
  
               ResultCode resultCode = admin.DeleteQueue(Qmgr, Qname);  
  
               if ((resultCode & ResultCode.QueueDeleted) == ResultCode.QueueDeleted)  
               {  
                   Console.WriteLine("Queue successfully deleted.");  
               }  
               if ((resultCode & ResultCode.QueueDoesNotExist) == ResultCode.QueueDoesNotExist)  
               {  
                   Console.WriteLine("Queue did not exist anyway!");  
               }  
           }  
  
       }  
   }  
   ```  
  
3. Add a reference to this project to the **MQSAgent 1.0 Type Library**. The **MQSAgent 1.0 Type Library** is available on the **COM** tab of the **Add reference** dialog box.  
  
   > [!NOTE]
   >  The MQSAgent COM+ component must be installed on the computer that you are running this console application from. For more information about installing the MQSAgent COM+ component see [Using the MQSAgent COM+ Configuration Wizard](../core/using-the-mqsagent-com-configuration-wizard.md).  
  
4. Build the console application.  
  
5. Open a command prompt in the same directory as the compiled console application.  
  
6. Type the name of the compiled console application with the appropriate arguments and press ENTER. For example, to delete the queue **testq** for the Queue Manager **QM_Test** you would type the following text at the command prompt and press ENTER:  
  
   ```  
   MQSeriesQueues d QM_Test testq  
   ```  
  
7. To create the queue **testq** for the Queue Manager **QM_Test** you would type the following text at the command prompt and press ENTER:  
  
   ```  
   MQSeriesQueues c QM_Test testq  
   ```