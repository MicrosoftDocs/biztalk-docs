---
title: "Lesson 1: Adding Flat File Receive Port and Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive locations, creating"
  - "creating, receive locations"
  - "receive ports, creating"
  - "creating, receive ports"
ms.assetid: 881f58d8-f541-4a85-b534-cb1ca627c002
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 1: Adding Flat File Receive Port and Location
The receive port always has an associated receive location that you must configure when you add the receive port. A receive location defines a specific address for an incoming message and the pipeline that you use to process the message.  
  
### To add a receive port  
  
1. In the BizTalk Server Administration Console, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  
  
2. In the Receive Port Properties dialog box, in the **Name** box, type **MT103_FlatFile_ReceivePort**.  
  
3. Click **Apply** to bind the port, and then click **OK**.  
  
4. In the BizTalk Server Administration Console, right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.  
  
5. In the Select a Receive Port dialog box, click **MT103_FlatFile_ReceivePort**, and then click **OK**.  
  
6. In the Receive Location Properties dialog box, in the **Name** box, type **MT103_FlatFile_ReceiveLocation**.  
  
7. In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.  
  
8. Click the **Configure** button to the right of the Type drop-down list.  
  
9. In the FILE Transport Properties dialog box, click **Browse**.  
  
10. In the Browse For Folder dialog box, move to the **\<drive\>:\Labs\Inbound** folder, and then click **Make New Folder**.  
  
11. Create a **FlatFile** folder in **\<drive\>:\Labs\Inbound**, and then click **OK**.  
  
12. In the **File mask** box, type **\*.txt**, and then click **OK**.  
  
13. In the Receive Location Properties dialog box, ensure that **BizTalkServerApplication** is entered for the **Receive handler** box.  
  
14. For the **Receive Pipeline** box, select **MT103ReceivePipeline** from the drop-down list.  
  
15. Click **Apply**, and then click **OK**.  
  
16. In the BizTalk Server Administration Console, click **Receive Locations**, right-click **MT103_FlatFile_ReceiveLocation**, and then click **Enable**.  
  
    Proceed to [Lesson 2: Adding an XML Send Port](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-an-xml-send-port.md).