---
title: "Step 10: Verify the End-to-End Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "end-to-end tutorial, verifying solution"
ms.assetid: 24b74ba6-e303-4ab1-8a93-25a430e4894d
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 10: Verify the End-to-End Scenario
In this step, you verify the end-to-end scenario for this tutorial.  
  
### To verify the end-to-end tutorial scenario  
  
1. Click **Start**, point to **Programs**, point to **Accessories**, and then click **Command Prompt**.  
  
2. In the Command Prompt window, move to **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities**, and then press **Enter**.  
  
   > [!NOTE]
   >  If you cannot find an MLLP Utilities folder under the SDK folder, the MLLP test tools may not be installed. Open the Control Panel, and then open **Add or Remove Programs**. Select **Microsoft BizTalk \<version\> Accelerator for HL7**, and then select **Change**. In the BTAHL7 setup wizard, select **Modify**. Expand the **Adapter** folder to see whether the **MLLP Test Tool** has been installed. If not, install it.  
  
3. In the Command Prompt window, type **mllpreceive /p 14000**, and then press **Enter**. This runs the MLLP listener application listening to port 14000 and specifying the default EB, SB, and CR characters of the MLLP message, and displays any messages received to the screen.  
  
4. Start an additional command prompt by clicking **Start**, point to **Programs**, point to **Accessories**, and then click **Command Prompt**.  
  
5. In the second Command Prompt window, move to **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities**, and then press **Enter**.  
  
   > [!NOTE]
   >  The following step sends the message.  
  
6. In the Command Prompt window, type **mllpsend /SB 11 /EB 28 /CR 13 /f "\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\ADT^A03.txt"**, where \<*drive*\> is your installation drive letter. Press **Enter**.  
  
7. Verify that you have the following results:  
  
   -   The MLLP listener application should display a message. The first line of the message should have the following values:  
  
       ```  
       MSH|^~\&|BTAHL7^IE^UUID|MCM|HI^System^GUID||199601121005||ADT^A04|000001|P|2.4|||SU|NE  
       ```  
  
   -   A message appears in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendMsg_RX. This message should be the same as the message shown by the MLLP listener application. Verify that the first line of the message has the same message values as follows. Note that the values for MSH3 a nd MSH5 in the following code match the values you specified for the Tutorial_RXSystem:  
  
       ```  
       MSH|^~\&|BTAHL7|MCM|Tutorial_RXSystem||199601121005||ADT^A03|000001|P|2.3.1  
       ```  
  
   -   Two messages appear in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendAck_ADT. One of these messages is an application acknowledgment; the other is a commit acknowledgment. The application acknowledgment should have the following content:  
  
       ```  
       MSH|^~\&|BTAHL7InterfaceEngine||Tutorial_ADTSystem|MCM|<datetime>||ACK^A03^ACK|000001|P|2.3.1|||AL  
       MSA|AA|000001  
       ```  
  
   -   The commit acknowledgment should have the following content:  
  
       ```  
       MSH|^~\&|BTAHL7InterfaceEngine||Tutorial_ADTSystem|MCM|<datetime>||ACK^A03^ACK|100000|P|2.3.1  
       MSA|CA|000001  
       ```  
  
   > [!NOTE]
   >  If the messages do not appear correctly, use the Health and Activity Tracking (HAT) tool to troubleshoot the error.  
  
   Congratulations! You have successfully completed the BTAHL7 End-to-End Tutorial.  
  
## See Also  
 [End-to-End Tutorial](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)