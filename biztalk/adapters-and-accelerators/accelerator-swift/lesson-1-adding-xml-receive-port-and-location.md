---
title: "Lesson 1: Adding XML Receive Port and Location | Microsoft Docs"
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
ms.assetid: 252bc080-3820-44cc-8749-715869f3f684
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 1: Adding XML Receive Port and Location
A receive port is a logical grouping of similar receive locations. A receive location defines a specific address (such as a URL or file location) for an incoming message and the pipeline that is used to process the message.  
  
### To add a receive port  
  
1. Start **BizTalk Server Administration** console.  
  
   > [!NOTE]
   >  The BizTalk Server Administration Console can also be opened from within Visual Studio by clicking **BizTalk Server Administration** in the **Tools** menu.  
  
2. In the BizTalk Server Administration Console, expand the **BizTalk Server Administration** node, then the **BizTalk Group** node, then the **Applications** node, and then the **BizTalk Application 1** node.  
  
3. Right-click **Receive Ports**, point to **New**, and then click **One-Way Receive Port**.  
  
4. In the Receive Port Properties dialog box, in the **Name** box, type **MT103_XML_ReceivePort**.  
  
5. Click **Apply** to bind the port, and then click **OK.**  
  
6. Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.  
  
7. In the Select a Receive Port dialog box, click **MT103_XML_ReceivePort**, and then click **OK**.  
  
8. In the Receive Location Properties dialog box, in the **Name** box, type **MT103_XML_ReceiveLocation**.  
  
9. In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.  
  
10. Click the **Configure** button to the right of the Type drop-down list.  
  
11. In the FILE Transport Properties dialog box, click **Browse**. Move to the **\<drive\>:\Labs** folder, and then click **Make New Folder**.  
  
12. In the Browse For Folder dialog box, create an **Inbound** folder in **\<drive\>:\Labs**, and then create an **XMLFile** folder in **\<drive\>:\Labs\Inbound**. Click **OK**.  
  
13. In the FILE Transport Properties dialog box, ensure that **\*.xml** is entered in the **File Mask** box, and then click **OK**.  
  
14. In the Receive Location Properties dialog box, ensure that **BizTalkServerApplication** is entered for the **Receive handler** box.  
  
15. For the **Receive Pipeline** box, select **XMLReceive** from the drop-down list.  
  
16. Click **Apply**, and then click **OK**.  
  
17. In the BizTalk Server Administration Console, click **Receive Locations**, right-click **MT103_XML_ReceiveLocation**, and then click **Enable**.  
  
    > [!NOTE]
    >  After you enable the receive location, BizTalk actively polls your file folder.  
  
    Proceed to [Lesson 2: Adding the Flat File Send Port](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-a-flat-file-send-port.md).