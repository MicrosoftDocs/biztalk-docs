---
title: "Lesson 2: Adding an XML Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send ports, XML ports"
  - "XML ports"
ms.assetid: 03b2ee43-7874-4ef9-b716-8e16e96d8382
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 2: Adding an XML Send Port
You use a send port to define how you want the messages sent. In this lesson, you create a send port to define how XML messages should be sent.  

### To add an XML send port  

1. In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

2. In the Send Port Properties dialog box, in the **Name** box, type **MT103_XML_SendPort**.  

3. In the **Transport** section, for the **Type** box, click the drop-down list, and then select **FILE**.  

4. Click the **Configure** button to the right of the Type drop-down list.  

5. In the FILE Transport Properties dialog box, click **Browse**.  

6. In the Browse For Folder dialog box, move to the **\<drive\>:\Labs\Outbound** folder, and then click **OK**.  

7. In the FILE Transport Properties dialog box, ensure that **%MessageID%.xml** is entered in the **File Name** box, and then click **OK**.  

8. In the Send Port Properties dialog box, ensure that **BizTalkServerApplication** is selected for the **Send handler** box, and that **PassThruTransmit** is selected for the **Send pipeline** box.  

9. In the left pane, click **Filters**, and then do the following:  


   |   Use this   |              To do this              |
   |--------------|--------------------------------------|
   | **Property** |   Select **BTS.ReceivePortName**.    |
   | **Operator** |            Select **==**.            |
   |  **Value**   | Type **MT103_FlatFile_ReceivePort**. |
   |  **Group**   |           Select **And**.            |


10. Click inside the next property line and do the following:  

    |Use this|To do this|  
    |--------------|----------------|  
    |**Property**|Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**|  
    |**Operator**|Select **==**.|  
    |**Value**|Type **False** for valid messages.|  

    > [!NOTE]
    >  You add the **"Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed == False"** filter expression clause so that the send port sends only successfully parsed and validated messages. Unlike a receive pipeline using native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] disassemblers, the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] disassembler will not suspend a failed (erroneous) message, but instead publishes it to the MessageBox and marks it as failed, using promoted properties. A4SWIFT attaches an XML representation of the errors that were collected to the failed message before publishing it to the MessageBox.  
    > Without including the "Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed == False" filter expression clause, your send port will send all messages: passed or failed. For more information about failed message subscriptions, see [Working with Failed Message Subscriptions](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).  

11. Click **Apply**, and then click **OK**.  

12. In the BizTalk Server Administration Console, in **Send Ports**, right-click **MT103_XML_SendPort**, and then click **Start**.  

    Proceed to [Module 6: Deploying the Business Rules](../../adapters-and-accelerators/accelerator-swift/module-6-deploying-the-business-rules.md).