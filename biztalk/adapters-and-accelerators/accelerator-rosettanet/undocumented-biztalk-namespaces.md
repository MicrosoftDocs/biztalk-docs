---
title: "Undocumented BizTalk Namespaces | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "undocumented BizTalk namespaces"
  - "technical reference, undocumented BizTalk namespaces"
ms.assetid: 58b0537a-4520-4de5-ae26-2ab69227a66a
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Undocumented BizTalk Namespaces
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] contains several BizTalk projects. These projects include namespaces and classes that you can interact with like a traditional namespace. However, most users interact with the BizTalk namespaces by adding them as references to BizTalk projects in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]®[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] and not through code. Therefore, the following namespaces are not fully documented in this release of [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]:  
  
-   [Microsoft.Solutions.BTARN.CommonTypes](<!-- TODO: review code entity reference <xref:assetId:///Microsoft.Solutions.BTARN.CommonTypes?qualifyHint=False&amp;autoUpgrade=True>  -->)  
  
     Contains helper orchestrations for public processes. Also contains the pipeline for processing RNIF messages.  
  
-   [Microsoft.Solutions.BTARN.Pipelines](<!-- TODO: review code entity reference <xref:assetId:///Microsoft.Solutions.BTARN.Pipelines?qualifyHint=False&amp;autoUpgrade=True>  -->)  
  
     Contains the Receive and Send pipelines that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses to receive and send messages.  
  
-   [Microsoft.Solutions.BTARN.PrivateInitiator](<!-- TODO: review code entity reference <xref:assetId:///Microsoft.Solutions.BTARN.PrivateInitiator?qualifyHint=False&amp;autoUpgrade=True>  -->)  
  
     Describes the default private initiator supplied by [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] that initiates the messaging sequence.  
  
-   [Microsoft.Solutions.BTARN.PrivateResponder](<!-- TODO: review code entity reference <xref:assetId:///Microsoft.Solutions.BTARN.PrivateResponder?qualifyHint=False&amp;autoUpgrade=True>  -->)  
  
     Contains the private responder that receives the first message from the private initiator.  
  
-   [Microsoft.Solutions.BTARN.PublicInitiator](<!-- TODO: review code entity reference <xref:assetId:///Microsoft.Solutions.BTARN.PublicInitiator?qualifyHint=False&amp;autoUpgrade=True>  -->)  
  
     Contains the main public orchestrations for [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].  
  
-   [Microsoft.Solutions.BTARN.PublicResponder](<!-- TODO: review code entity reference <xref:assetId:///Microsoft.Solutions.BTARN.PublicResponder?qualifyHint=False&amp;autoUpgrade=True>  -->)  
  
     Contains the public responder to the public orchestrations.