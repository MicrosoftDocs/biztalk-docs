---
title: "Testing Your Installation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "testing installation"
  - "installing, testing installation"
ms.assetid: db27a75c-db7f-46ff-b8ef-2624ff18dcc8
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Testing Your Installation
You can set up your [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] installation for testing either by manually running through the end-to-end tutorial or by executing the end-to-end tutorial program. To exercise the program, either click the **Launch Tutorial** button during setup or execute EndToEndTutorial.exe in the C:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial folder (after running installation and configuration). Either of these automated actions will perform the same setup steps that you would manually perform by running through the tutorial. The end-to-end tutorial program does the following:  
  
- Deploys MSH and ACK schemas  
  
- Deploys Version 2.3.1 common schemas  
  
- Deploys ADT schemas  
  
- Creates the Tutorial_1WayReceive receive port  
  
- Creates the Tutorial_MLLPReceive receive location  
  
- Creates the Tutorial_BTAHL7PickUp receive port  
  
- Creates the Tutorial_FileReceiveLoc receive location  
  
- Creates the Tutorial_sendAck_ADT send port  
  
- Creates the Tutorial_sendMsg_RX send port  
  
- Creates the Tutorial_BTAHL7Drop send port  
  
- Creates the Tutorial_MLLPSend send port  
  
- Creates the Tutorial_ADTSystem party  
  
- Creates the Tutorial_RXSystem party  
  
- Creates the Tutorial_HISystem party  
  
- Restarts the BizTalk Service  
  
  If you have executed the end-to-end tutorial program, you can drop a test instance for HL7 in a pre-defined folder. The receive pipeline associated with the folder picks up the message and processes it. Based on filters, a send pipeline routes the document to the destination folder. This simple "round-trip" exercises the basic building blocks of the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) engine and confirms your installation.  
  
### To test your installation  
  
1. Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial folder.  
  
2. Right-click the **TutorialSampleInstance.txt** file, and then click **Copy**.  
  
3. Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7PickUp folder.  
  
4. Right-click the folder, and then click **Paste**.  
  
5. Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop folder.  
  
    You can verify if your installation was successful if the processed instance appears in the **Tutorial_BTAHL7Drop** folder as \<*Guid*\>.txt.  
  
   Proceed to the next step, [Preparing to Use the Tutorial](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md).