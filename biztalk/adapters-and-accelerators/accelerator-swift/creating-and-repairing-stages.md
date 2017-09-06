---
title: "Creating and Repairing Stages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "stages, repair"
  - "stages, create"
ms.assetid: 07d7ce7b-ed15-40a7-9c85-280a1d38985b
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating and Repairing Stages
The first stage in any workflow can be either a Create or Repair stage, that is, roles that have a capability defined as create or repair. The message originates from the BizTalk MessageBox as a failed message or an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user manually creates a message through the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms.  
  
 The original message creator or repairer is the first digital signer of the message, and adds his or her digital signature to the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form after creating or repairing the message. This first signature not only proves the identity of the message creator or repairer, but also locks the contents of the message in its current state. If the message is altered after the first signing, the digital signature stack is broken and warnings are shown to the user stating that the digital signatures on the form are invalid.