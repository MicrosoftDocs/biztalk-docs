---
title: "Large Message to MSMQ | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1fb87b46-5656-42c0-be99-8ab66e51bb4d
caps.latest.revision: 35
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Large Message to MSMQ
The Large Message to MSMQ sample demonstrates how to send an .xml document larger than 4 megabytes (MB) from Message Queuing (also known as MSMQ) to the BizTalk MSMQ adapter by using the **MQSendLargeMessage** API implemented by MQRTLarge.dll.  
  
## What This Sample Does  
 The sample works as follows:  
  
1. A user uses SendLargeMessage.exe to send a large .xml file to a queue on a local computer.  
  
2. BizTalk Server receives the large .xml file from the queue and copies it to a local directory.  
  
   Many operations in Message Queuing are asynchronous. That is, many MSMQ API calls (for example, **MQSendLargeMessage**) return to the caller before the requested operation has fully completed.  
  
   MSMQ provides a mechanism to deliver feedback to the application after the operation has completed. This mechanism involves the use of an "Admin Queue." MSMQ returns feedback in the form of a message in the Admin Queue. The Admin Queue to which MSMQ will return feedback is specified when the original MSMQ API call is made. So, for example, when sending a message using the **MQSendLargeMessage** API, the application can specify the name of an Admin Queue by using the **PROPID_M_ADMIN_QUEUE** message property on the message passed in the call to **MQSendLargeMessage**. Even though the application may get a successful return code on the **MQSendLargeMessage** call, if the message send operation subsequently fails, MSMQ writes a message to that effect to the specified Admin Queue.  
  
   If the application does not specify an Admin Queue, a send failure results in the message being lost and no diagnostics captured — in effect, the message disappears without any evidence. A number of error situations in MSMQ can cause this to happen, for example, doing a non-transactional send to a transactional queue.  
  
   In the context of this sample, it is important that the code specify a transaction type in the call to **MQSendLargeMessage** that is consistent with the transaction support specified for the queue to which the message is sent. If this is not done and if no Admin Queue is specified (as is the case in this sample), then MSMQ discards the sent message with no indication that it has done so (that is, no error code returned to the application, no diagnostics written to the event log, and so on).  
  
## Where to Find This Sample  
 \<Samples Path\>\AdaptersUsage\MSMQLarge  
  
> [!NOTE]
>  If using a 64-bit version of Windows and BizTalk Server, the sample will be installed in the **C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\SDK\Samples\AdaptersUsage\MSMQLarge** folder.  Note this change for any other instructions in this document using the **C:\Program Files** folder.  
  
 The following table shows the files in this sample and describes their purpose.  
  
|**File**|**Description**|  
|--------------|---------------------|  
|**MQRTLarge.dll**|Provides an add-on for native message queuing. Exposes the **MQSendLargeMessage** and **MQReceiveLargeMessage** APIs.<br /><br /> You must install BizTalk Server on a 64-bit version of Windows in order to access the 64-bit version of MQRTLarge.dll.<br /><br /> For an MSMQ solution without BizTalk Server, the MQRTLarge.dll may still function correctly. However, this is not a recommended configuration that Microsoft supports, and unexpected results may occur if used outside of the BizTalk Server environment.|  
|||  
|**LargeMessages.sln**|Provides a Visual Studio solution to create the SendLargeMessage executable used in the sample.|  
|**XMLCreator.sln**|Provides a Visual Studio solution to create the XMLCreator executable to generate a test .xml file for the SDK sample.|  
  
## Configure BizTalk and Create the MSMQ Queue  
 Ensure that Visual Studio, Microsoft Message Queuing, and BizTalk Server installed.  
  
#### To configure BizTalk Server  
  
1. In Visual Studio, open the **C:\Program Files\Microsoft BizTalk Server \<version\>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeMessages.sln** solution file.  Build the sample.  
  
2. Create a **C:\Demo** directory where BizTalk Server will place the messages from MSMQ.  
  
3. Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
4. Create a send port for the sample to write the message.  
  
   -   Expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, right-click **Send Ports**, click **New**, and then click **Static One-Way Send Port**.  
  
5. In the **Static One-Way Send Port Properties** dialog box, set the name of the port to **MySendPort**.  
  
6. Set the transport type to **File**.  
  
7. Click the **Configure** button to open the **File Transport Properties** form. Enter **C:\Demo** in **Destination Folder**. Ensure that the host instance identity has access to the C:\Demo folder.  
  
8. Ensure that **File Name** is set to **%MessageID%.xml**. Click **OK**.  
  
9. Click **Filters**.  
  
    1.  Set **Property** to **BTS.ReceivePortName**.  
  
    2.  Set **Operator** to **=**.  
  
    3.  Set **Value** to **MyReceivePort**.  
  
    4.  Click **OK**.  
  
10. Create a receive port to accept the message from MSMQ.  
  
    1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **Receive Ports**.  
  
    2. Click **New**, and then click **One-way Receive Port**.  
  
11. In the **Receive Port Properties** dialog box, set the name of the port to **MyReceivePort**, and then click **OK**.  
  
12. After creating a receive port for the sample, you must create a receive location.  
  
    1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **Receive Locations**.  
  
    2. Click **New**, and then click **One-way Receive Location**.  
  
    3. Set the name of the receive location to **MSMQReceiveLocation**.  
  
    4. In the **Select a Receive Port** dialog box, select **MyReceivePort**.  
  
    5. In the **Receive Location Properties** dialog box, set **Transport Type** to **MSMQ**.  
  
    6. In the **Address (URI)** section, click **Configure** to open the **MSMQ Transport Properties** form. Set **Queue** to **localhost\private$\test**.  
  
    7. Set **Transactional** to `True`, and then click **OK**.  
  
13. You must make the ports and receive locations available for use through the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
    1.  Right-click **MySendPort**, and then click **Enlist**.  
  
    2.  Right-click **MySendPort**, and then click **Start**.  
  
    3.  Right-click **MSMQReceiveLocation**, and then click **Enable**.  
  
#### To create the MSMQ queue in Windows Server
  
1.  Click **Start**, right-click **Computer**, and then click **Manage**.  
  
2.  Expand the **Features** node.  
  
3.  Expand the **Message Queuing** node.  
  
4.  Right-click the **Private Queues** node, click **New**, and then click **Private Queue**.  
  
5.  Under **Queue name**, enter **test**. Ensure that the **Transactional** check box is selected.  
  
6.  Click **OK**.  
  
#### To create the MSMQ queue in Windows 
  
1.  Click **Start**, right-click **Computer**, and then click **Manage**.  
  
2.  Expand **Services and Applications**, and then expand the **Message Queuing** node.  
  
    > [!NOTE]
    >  If **Message Queuing** is not installed in the computer, go to **Control Panel > Programs > Programs and Features**, and then select **Turn Windows features on or off**. Check all the features under **Microsoft Message Queue (MSMQ) Server**, and then click **OK**.  
  
3.  Right-click the **Private Queues** node, click **New**, and then click **Private Queue**.  
  
4.  Under **Queue name**, enter **test**. Ensure that the **Transactional** check box is selected.  
  
5.  Click **OK**.  
  
## Creating a Test File and Running the Sample  
  
#### To create a large test file  
  
1.  In Visual Studio, open the solution **C:\Program Files\Microsoft BizTalk Server \<version\>\SDK\Samples\AdaptersUsage\MSMQLarge\XMLCreator\XMLCreator.sln**.  
  
2.  Build and run the project.  
  
3.  Under **XML Body**, type **This is a test message**.  
  
4.  Under **# of times to copy XML body**, type `250000`.  
  
5.  Under **XML File Location**, type `C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeFile.xml`.  
  
6.  Click **Create XML**, and then click **OK**.  
  
#### To run the sample  
  
1.  Open a command prompt and change directory to **C:\Program Files\Microsoft BizTalk Server \<version\>\SDK\Samples\AdaptersUsage\MSMQLarge\SendLargeMessage\bin\debug**.  
  
2.  At the command prompt, run **SendLargeMessage.exe**. The SendLargeMessage executable accepts two variables — the first is the location of the MSMQ queue, and the second is the location of the .xml file to send:  
  
    ```  
    DIRECT=OS:localhost\private$\Test  "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeFile.xml"  
    ```  
  
3.  Verify that a file of the same size was created on the BizTalk Server computer in the **C:\Demo** directory. This is the directory you identified in the MySendPort send port.  
  
## Comments  
 SendLargeMessage.exe references the **LargeMessages** API, which in turn references the BizTalk Message Queuing Large Message Extension (MQRTLarge.dll) API. The Message Queuing Large Message Extension API is an add-on for native message queuing that enables the processing of messages larger than the 4 MB limit of native message queuing.  
  
 This sample uses the **MQSendLargeMessage** API and exposes the API to the .NET Framework by using the **LargeMessages** API.  
  
## See Also  
 [BizTalk Message Queuing Large Message Extension](../core/biztalk-message-queuing-large-message-extension.md)   
 [Adapter Samples - Usage](../core/adapter-samples-usage.md)