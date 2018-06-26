---
title: "Lesson 2: Submitting an MT103 Message That Is Not Valid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, invalid messages"
  - "submitting, invalid messages"
  - "submitting, MT103 messages"
  - "MT103 messages"
  - "messages, MT103 messages"
ms.assetid: 4b070ae1-c400-421a-b2f6-b7b1f22c0e41
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 2: Submitting an MT103 Message That Is Not Valid
In this lesson, you submit an MT103 message that is not valid and then you troubleshoot the resulting error using your System Tools.  
  
### To submit an MT103 message that is not valid  
  
1. Copy the file MT103_Invalid_Sample.txt from \<*drive:*\>\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial to \<*drive*\>:\Labs\Inbound\FlatFile folder. Note the time that you drop the file into the folder.  
  
2. Open \<*drive:*\>\Labs\Outbound to verify that no XML file corresponding to MT103_Invalid_Sample.txt is in the folder. (The XML file corresponding to the valid MT103_Sample.txt message should still be in that folder.)  
  
3. In Notepad, open the file MT103_Invalid_Sample.txt in \<*drive:*\>\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial.  
  
4. Start **BizTalk Server Administration**.  
  
5. In the BizTalk Server Administration Console, expand **Event Viewer (Local)**, and then click **Application**.  
  
6. Look for an error entry that has a source of BizTalk Accelerator for SWIFT and a time that corresponds to when you dropped the invalid message into the \<*drive*\>:\Labs\Inbound\FlatFile folder. Double-click that error entry.  
  
7. In the Event Properties dialog box for the error, verify in the Description pane that the failed message was published to the MessageBox and that the SWIFT Disassembler marked **A4SWIFT_Failed** as **True**. Close the Event Properties dialog box.  
  
8. In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, and then expand **BizTalk Group**. In the **View** menu, click **Group Hub Page**.  
  
9. In the **Group Overview** pane, in the **Grouped Suspended Service Instances** pane, click **Grouped by Application**.  
  
10. In the **Preview for the selected query result** pane, double-click the entry for **MT103_FlatFile_ReceivePort**.  
  
11. In the Service Details dialog box, click the **Messages** tab. Double-click the entry for which the Service Name is **MT103_FlatFile_ReceivePort**.  
  
12. In the Message Details dialog box, click **Body** in the left pane.  
  
13. Verify that the message displayed in the body pane of the Message Details dialog box corresponds to MT103_Invalid_Sample.txt that you opened in Notepad.  
  
    Proceed to [Lesson 3: Testing an XML Instance](../../adapters-and-accelerators/accelerator-swift/lesson-3-testing-an-xml-instance.md).