---
title: "SendMSMQMessage | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSMQ adapters, examples"
  - "examples, MSMQ adapters"
ms.assetid: 398bc396-0c66-4d55-886a-0d9bdab6476f
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SendMSMQMessage
The SendMSMQMessage sample demonstrates how to send a message to an MSMQ port from a .NET-based application. It also provides instructions about how to configure Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use an MSMQ receive location.  

 You should be aware that many operations in Message Queuing are asynchronous. That is, many MSMQ API calls (for example, **System.Messaging.MessageQueue.Send**) return to the caller before the requested operation has fully completed. MSMQ provides a mechanism to deliver feedback to the application after the operation has completed. This mechanism involves the use of an "Admin Queue." MSMQ returns feedback in the form of a message in the Admin Queue. The Admin Queue to which MSMQ will return feedback is specified when the original MSMQ API call is made. So, for example, when sending a message using the **System.Messaging.MessageQueue.Send** API, the application can specify the name of an Admin Queue by using the **PROPID_M_ADMIN_QUEUE** message property on the message passed in the call to **System.Messaging.MessageQueue.Send**. Even though the application may get a successful return code on the **System.Messaging.MessageQueue.Send** call, if the message send operation subsequently fails, MSMQ writes a message to that effect to the specified Admin Queue. If the application does not specify an Admin Queue, the send failure results in the message being lost and no diagnostics captured — in effect, the message disappears without any evidence. There are a number of error situations in MSMQ that can cause this to happen, for example, doing a non-transactional send to a transactional queue.  

 In the context of this sample, it is important that the code specify a transaction type in the call to **System.Messaging.MessageQueue.Send** that is consistent with the transaction support specified for the queue to which the message is sent. If this is not done and if no Admin Queue is specified (as is the case in this sample), then MSMQ discards the sent message with no indication that it has done so (that is, no error code returned to the application, no diagnostics written to the event log, and so on).  

## Where to Find This Sample  
 \<Samples Path\>\AdaptersUsage\SendMSMQMessage\  

 The following table shows the files in this sample and describes their purpose.  


|                                 Files                                 |                                                                      Description                                                                       |
|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| App.ico, AssemblyInfo.cs, SendMSMQMessage.csproj, SendMSMQMessage.sln |                           Provide project, solution, and related files for the simple graphical application for this sample.                           |
|                         Form1.cs, Form1.resx                          | Provide Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].NET source and form files for the simple graphical application for this sample. |

## How to Use This Sample  
 You can use the code in the simple graphical application included with this sample as an example of how to send messages to MSMQ receive locations within [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] from .NET-enabled applications such as Microsoft Office, from ASP.NET pages, and so on.  

## Building and Initializing the Sample  

#### To build the sample executable  

1. Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file SendMSMQMessage.sln.  

2. On the **Build** menu, click **Build Solution**.  

## Configuring BizTalk Server and Creating the MSMQ Queue  
 Use the following procedures to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and create the MSMQ queue for running the sample.  

#### To create the MSMQ queue in Windows Server 2008 R2 or Windows Server 2008 SP2  

1.  Click **Start**, right-click **Computer**, and then click **Manage**.  

2.  Expand the **Features** node.  If **Message Queuing** is not installed, right-click **Features** and select **Add Features**.  Check **Message Queuing**, click **Next**, and then click **Install** to install MSMQ on that system.  

3.  Expand the **Message Queuing** node.  

4.  Right-click the **Private Queues** node, click **New**, and then click **Private Queue**.  

5.  Under **Queue name**, enter `test`. Ensure that the **Transactional** check box is selected.  

6.  Click **OK**.  

#### To create the MSMQ queue in Windows 7 or Windows Vista SP2  

1.  Click **Start**, right-click **Computer**, and then click **Manage**.  

2.  Expand **Services and Applications**, and then expand the **Message Queuing** node.  

    > [!NOTE]
    >  If **Message Queuing** is not installed in the computer, go to **Control Panel > Programs > Programs and Features**, and then select **Turn Windows features on or off**. Check all the features under **Microsoft Message Queue (MSMQ) Server**, and then click **OK**.  

3.  Right-click the **Private Queues** node, click **New**, and then click **Private Queue**.  

4.  Under **Queue name**, enter **test**. Ensure that the **Transactional** check box is selected.  

5.  Click **OK**.  

#### To configure BizTalk Server  

1. Select a folder in which to receive messages. The following steps assume that you have selected C:\Demo\Report, but you can adjust the steps as necessary for another folder.  

2. Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  

3. Create a new application named **MSMQSample**.  

4. Right-click **Receive Ports**, click **New**, and then click **One-way Receive Port**.  

5. In the **Receive Port Properties** dialog box, in the **Name** box enter **MyReceivePort**, and then click **OK**.  

6. Right-click **Receive Locations**, click **New**, and then click **One-way Receive Location**. In the **Select a Receive Port** dialog box, select the receive port you just created and click **OK**.  

7. In the **Receive Location Properties** dialog box, in the **Name** box, type a name for the receive port, such as **MSMQReceiveLocation**.  

8. In the **Receive Location Properties** dialog box, for the transport type, select **MSMQ** .  

9. Click **Configure** to open the **MSMQ Transport Properties** dialog box. Set **Queue** to `localhost\private$\test`, set **Transactional** to `True`, and then click **OK**.  

10. Expand the application, select **Send Ports**, select **New**, select **Static One-way Send Port**.  

11. In the **Send Port Properties** dialog box, in the **Name** box, type a name for the send port, such as **MySendPort**.  

12. Set the **Transport Type** property to **FILE**.  

13. Click **Configure** to open the **File Transport Properties** dialog box.  

14. In the **FILE Transport Properties** dialog box, set the **Destination Folder** property to **C:\Demo\Report**, keep the default settings for the other properties, and then click **OK**.  

15. Select **Filters**, and then add a new row by setting **Property** to **BTS.ReceivePortName**. Leave the **Operator** column set to **==**, set the **Value** column to **MyReceivePort**, and then click **OK**.  

16. Right-click your new send port, and then click **Enlist**.  

17. Right-click your new send port again, and then click **Start**.  

18. Right-click your new receive location, and then click **Enable**.  

    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is now ready to work with this sample.  

## Running the Sample  
 Use the following procedure to run the SendMSMQMessage sample.  

#### To run the sample  

1. In a command window, navigate to the following folder:  

    \<Samples Path\>\AdaptersUsage\SendMSMQMessage\bin\Debug  

2. Run the file SendMSMQMessage.exe, which starts the graphical application that provides the user interface for this sample.  

3. In the graphical application, in the **BizTalk machine name** box, type the name of the local computer.  

4. Try the **Send Wrapped** option:  

   1. Optionally change the text in the **Message body** box.  

   2. Click **Send wrapped**.  

      If the operation succeeds, you will see the following:  

   - The word **Success** appears in red font in the box immediately above the buttons.  

   - A file appears in your destination folder, C:\Demo\Reports. This file contains the text from the **Message body** box wrapped in simple XML tags by the .NET message queuing library.  

     If the operation fails, you will see an error message in the box immediately above the buttons.  

5. Try the **Send Exact** option:  

   1. Optionally change the text in the **Message body** box.  

   2. Click **Send exact**.  

      If the operation succeeds, you will see the following:  

   - The word **Success** appears in red font in the box immediately above the buttons.  

   - A file appears in your destination folder, C:\Demo\Reports. This file contains the text from the **Message body** box exactly as it appears in the text box.  

     If the operation fails, you will see an error message in the box immediately above the buttons.  

## See Also  
 [Adapter Samples - Usage](../core/adapter-samples-usage.md)