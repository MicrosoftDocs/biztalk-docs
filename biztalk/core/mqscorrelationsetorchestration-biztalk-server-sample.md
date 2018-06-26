---
title: "MQSCorrelationSetOrchestration (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "examples, MQSeries adapters"
  - "orchestrations, examples"
  - "examples, orchestrations"
  - "examples, messages"
  - "messages, examples"
  - "MQSeries adapters, examples"
ms.assetid: fcda65d0-e3ec-4ead-978d-3904903b8762
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MQSCorrelationSetOrchestration (BizTalk Server Sample)
The MQSCorrelationSetOrchestration sample demonstrates how to use the MQSeries correlation identifier for correlating messages sent to an MQSeries queue back to a running orchestration. The orchestration sets the MQSeries correlation identifier and message identifier values using the **MQMD_CorrelId** and **MQMD_MsgID** properties. The MQSeries Queue Manager copies the MessageID value to the CorrelationID property of the message.  

## Prerequisites  
 This sample assumes that you have installed IBM WebSphere MQSeries on the same server that you are running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

## What This Sample Does  
 This sample illustrates how to set a message identifier and correlation identifier in a message sent to an IBM WebSphere MQSeries Server. This is one method that can be used to correlate a message back to a running orchestration instance. When the MQSeries Queue Manager receives the message it copies the MessageID value to the CorrelationID property of the message. This CorrelationID (**MQMD_CorrelId**) is then used in the orchestration to associate the response message on MQSeries with the instance used to send messages to MQSeries.  

## How This Sample is Designed and Why  
 This sample illustrates a scenario in which a document that is being processed by an orchestration can be sent to an MQSeries queue (presumably for additional processing) and returned back to the running orchestration.  

## Where to Find This Sample  
 *\<Samples Path\>*\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestration  

 The following table shows the files in this sample and describes their purpose.  

|**File**|**Description**|  
|--------------|---------------------|  
|**MQSCorrelationSetOrchestration.btproj,**<br /><br /> **MQSCorrelationSetOrchestration.sln**|Project and solution files for the application.|  
|**MQSCorrelationSetOrchestration.odx**|The orchestration of the application.|  
|**MQSCorrelationSetOrchestration.snk**|The strong naming key file.|  
|**Setup.bat**|Builds and initializes this sample.|  

## How to Use This Sample  
 Incorporate the logic employed in this sample if you need to send a message to MQSeries Server as one of the steps in overall workflow.  

### To create the MQSeries queue through the WebSphere MQ Explorer  

1.  Click **Start**, point to **Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.  

2.  Double-click **Queue Managers**, and then double-click the default queue manager. The default queue manager is typically named **QM_<machine_name>** where *machine_name* is the name of your computer.  

3.  Right-click **Queues**, point to **New**, and then click **Local Queue**.  

4.  In **Create Local Queue** dialog box, in **Queue Name**, type "MQCorrelation", and then click **OK**.  

### To create the receive location and the MQSeries queue  

1.  Open the BizTalk Server Administration console.  

2.  Expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the required application.  

3.  Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  

4.  In the **One-way Receive Port Properties** dialog box, in the **Name** box type "MQIn" and click **OK**.  

5.  In the left pane, click **Receive Locations** tab, and then click **New**.  

6.  In the **Receive Location Properties** dialog box, in the **Name** box, type "MQIn".  

7.  In the **Transport Type** box, select **MQSeries**.  

8.  In the **Receive Handler** box, select **BizTalkServerApplication**.  

9. In the **Receive pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.  

10. Click **Configure**.  

11. In the **MQSeries Transport Properties** dialog box, in the **Polling Interval** box, type "10".  

12. In the **Queue Definition** box, click the ellipsis (…) button.  

13. In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.  

14. In the **Queue Manager** box, select the default queue manager.  

15. In the **Queue** box, type "MQCorrelation", and then click **Export**.  

16. In the **Export** dialog box, click **Create Queue**, and then click**OK**or **Done** until you have exited all dialog boxes.  

### To create the send port to MQSeries  

1.  Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

2.  In the **Send Port Properties** dialog box, in the **Name** box, type "MQOut".  

3.  In the **Transport Type** box, select **MQSeries**.  

4.  In the **Send pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.  

5.  Click **Configure**.  

6.  In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** box, click the ellipsis (…) button.  

7.  In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.  

8.  In the **Queue Manager** box, select the default queue manager.  

9. In the **Queue** box, type "MQCorrelation", and then click **OK**.  

10. Click **OK** until you have exited all dialog boxes.  

### To enable the receive location and start the send port  

1.  In the BizTalk Server Administration console, click **Receive Ports**.  

2.  In the details pane, right-click the **MQIn** receive location and click **Enable**.  

3.  In the details pane, right-click the **MQOut** send port and click **Start.**  

### To create the folders used by the application  

1.  On your **C:\\** drive, create a folder named "temp" if it does not already exist.  

2.  Under the **C:\temp** directory, create folders named "Pickup" and "Dropit".  

### Building and deploying this sample  

1.  In a command window, navigate to the following folder:  

     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestration`  

2.  Run the file Setup.bat, which performs the following actions:  

    1.  Creates a strong name key for the project.  

    2.  Compiles and deploys the orchestration project.  

    3.  Creates a send port and a receive port with the File adapter.  

### Bind and start the Orchestration  

1.  In the BizTalk Server Administration console, expand the **Orchestrations** folder.  

2.  In the details pane, right-click the **MQSCorrelationSetOrchestration** orchestration, and then click **Bind**.  

3.  Bind the orchestration ports to the following send ports and receive locations:  

    |**Orchestration Port**|**Messaging Port / Receive Location**|  
    |----------------------------|--------------------------------------------|  
    |FileReceivePort|MQSCorrelationSetOrchestration.FileReceivePort|  
    |MQSeriesResponseReceivePort|MQIn|  
    |MQSeriesRequestSendPort|MQOut|  
    |FileSendPort|MQSCorrelationSetOrchestration.FileSendPort|  

4.  Click **Host**.  

5.  In the **Host** box, select **BizTalkServerApplication**, and click **OK**.  

6.  In **Send Ports**, right-click **MQSCorrelationSetOrchestration.FileSendPort**, and then select **Start**.  

7.  In **Receive Locations**, right-click **MQSCorrelationSetOrchestration.FileReceivePort** and then select **Enable**.  

8.  Right-click the orchestration and click **Start**.  

    > [!NOTE]
    >  Starting the orchestration also automatically enlists the orchestration.  

### To test the application  

1.  Put a file into the **C:\Temp\Pickup** folder.  

2.  Examine the file in the **C:\Temp\Dropit** folder.  

    > [!NOTE]
    >  If you disable the **MQIn** receive location, you can examine the message in WebSphere MQ Explorer and see that the message and correlation identifiers are set. To do this, launch the **WebSphere MQ Explorer** and examine the message placed in the **MQCorrelation** queue. The message and correlation identifiers are displayed on the **Identifiers** tab of the **Message properties** dialog box.  

    > [!NOTE]
    >  In a production scenario, you will want to assign a unique ID for each message that is sent to the MQSeries queue. This can be done by modifying the expression shape in the orchestration. Change the following lines to set these properties to a unique 24 byte ID:  
    >   
    >  MQSeriesRequestSendMessageModified(MQSeries.MQMD_MsgId) = "111213141516171819202122232425262728293031323334";  
    >   
    >  MQSeriesRequestSendMessageModified(MQSeries.MQMD_CorrelId) = "111213141516171819202122232425262728293031323334";  
    >   
    >  If you want to set a unique 24 byte ID for these properties see the section **To create a unique 24 byte ID for messages sent to MQSeries**.  

### To create a unique 24 byte ID for messages sent to MQSeries  

1. Create a new C# class library project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  

2. Paste the following code into the .cs file for the class:  

   ```  
   using System;  
   using System.Collections.Generic;  
   using System.Text;  
   using System.Security.Cryptography;  

   namespace MQId  
   {[Serializable]  
       public class GetId  
       {  
           RNGCryptoServiceProvider randomCryptoString = new RNGCryptoServiceProvider();  

           public string getGuidstr()  
           {  
               byte[] newGuid = GetRandomData(24);  
               return ConvertToHex(newGuid);  
           }  

           private byte[] GetRandomData(int keySize)  
           {  
               byte[] randomData = new byte[keySize];  
               randomCryptoString.GetBytes(randomData);  
               return randomData;  
           }  

           private string ConvertToHex(byte[] key)  
           {  
               StringBuilder hexString = new StringBuilder();  
               for (int i = 0; i < key.Length; ++i)  
               {  
                   hexString.Append(String.Format("{0:X2}", key[i]));  
               }  
               return hexString.ToString();  
           }  
       }  
   }  
   ```  

3. Specify a **Default namespace** of **MQId** and an **Assembly name** of **GetId** on the project properties **Application** page.  

4. Specify a strong name key file to sign the assembly on the project properties **Signing** page and then build the project.  

5. Use the global assembly cache tool (gacutil.exe) to load the compiled assembly into the GAC (gacutil /i \<*name of compiled dll file*\>).  

6. Add a reference to the GetId assembly in the BizTalk project for this sample.  

7. Add two variables to the orchestration used in this sample:  


   | Variable name (Identifier) |     Type      |
   |----------------------------|---------------|
   |           GetId            |  MQId.GetId   |
   |          strGuid           | System.String |


8. Paste the following code into the expression shape used in the orchestration for this sample, this code should overwrite the existing code:  

   ```  
   GetId = new MQId.GetId();  
   strGuid = GetId.getGuidstr();  
   MQSeriesRequestSendMessageModified = MQSeriesRequestSendMessage;  
   MQSeriesRequestSendMessageModified(MQSeries.MQMD_MsgId) = strGuid;  
   MQSeriesRequestSendMessageModified(MQSeries.MQMD_CorrelId) = strGuid;  
   ```  

9. Stop and remove the orchestration in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console if it is already deployed. Then follow the steps in the sections **Building and deploying this sample**, **Bind and start the Orchestration** and **To test the application**.  

    > [!NOTE]
    >  Use of this method to create a unique 24 byte ID for messages sent to MQSeries does not 100% guarantee unique IDs for all messages sent but the probability of duplicate message IDs is very low. If business needs require a 100% guarantee that no message IDs are duplicated then you will need to employ different custom code to ensure this functionality.  

## Classes or Methods Used in This Sample  
 This sample does not make explicit use of any classes or methods.  

## See Also  
 [Correlating Messages Using Request-Reply](../core/correlating-messages-using-request-reply.md)   
 [MQSeries Adapter Samples](../core/mqseries-adapter-samples.md)