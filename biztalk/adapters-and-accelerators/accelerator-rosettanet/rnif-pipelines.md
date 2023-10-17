---
description: "Learn more about: RNIF Pipelines"
title: "RNIF Pipelines | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RNIF, pipelines"
  - "pipelines, RNIF"
ms.assetid: 6cf480fe-6b54-4b13-8318-617f3bba71d0
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# RNIF Pipelines
The Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] receive and send pipelines perform the processing required for receive or send RosettaNet Implementation Framework (RNIF) messages. This processing includes preprocessing, decoding/encoding, decrypting/encrypting, disassembly/assembly, and party authentication.  
  
## Pipeline Files  
 Standard [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receive and send pipelines do not process RNIF messages natively. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] has added custom receive and send pipelines for this purpose. These pipelines are built on the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipelines, but add [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]-specific processing capability. The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipelines (RNIFReceive.btp and RNIFSend.btp) are available in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK at \<*drive*\>:\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines. This lets you customize them for your own purposes.  
  
## See Also  
 [BTARN Receive Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)   
 [BTARN Send Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)
