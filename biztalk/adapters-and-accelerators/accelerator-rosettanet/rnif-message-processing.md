---
description: "Learn more about: RNIF Message Processing"
title: "RNIF Message Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RosettaNet Implementation Framework (RNIF)"
  - "RosettaNet, about RosettaNet"
  - "RNIF"
  - "RNIF, non-repudiation"
  - "RNIF, BizTalk Accelerator for RosettaNet"
  - "non-repudiation"
  - "RNIF, about RNIF"
  - "BizTalk Accelerator for RosettaNet, RNIF"
  - "RosettaNet"
ms.assetid: 994f15bc-765c-4220-8ab1-176919e9e821
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# RNIF Message Processing
The RosettaNet organization defines message exchange in the RosettaNet Implementation Framework (RNIF) specifications. RNIF defines how integration systems will transport messages. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] fully implements the RNIF specifications, adding that functionality to what Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] natively provides out-of-the-box.  
  
RNIF communications are complex. The public processes that perform RNIF processing include a variety of validation checks and complex workflow logic. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] provides this functionality natively. This lets you use a RosettaNet-compliant system without developing or maintaining RNIF logic from scratch.  
  
## BTARN Support for RNIF  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] supports both versions of RNIF: RNIF 1.1 and RNIF 2.0 (V02.00.01). RNIF 2.0 added significant functionality beyond that supported by RNIF 1.1, including encryption, attachments, and synchronous transactions. RNIF 2.0 is not backward compatible with RNIF 1.1.  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] is RosettaNet Ready RNIF 2.0 compliant.  
  
The two versions define the RosettaNet message differently. For more information about the different message containers, see [RNIF Standard](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md).  
  
Integration systems perform RNIF transfer over HTTP/HTTPS and SMTP; however, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] implements only HTTP/HTTPS. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support attachments and synchronous transactions in RNIF 1.1.  
  
### Non-Repudiation  
The RNIF standard includes a requirement for non-repudiation. This involves storing the wire format of any message received or sent by [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] in a non-repudiation database, so that you can prove legally that you have received or sent it. For this purpose, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses the MessageStorageIn table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive database for incoming messages and the MessageStorageOut table in the same database for outgoing messages.  
  
You set non-repudiation requirements for service content and for acknowledgements separately in the process configuration profile. If you set one or both of the **Non-Repudiation of Origin and Content** and **Non-Repudiation Required** options to `True`, then [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will store the following data:  
  
|Data|Contents|  
|----------|--------------|  
|RecordID|Proprietary unique ID of the stored message|  
|MessageCategory|Request (0), Response (1), or Signal (2)|  
|DestinationParty|Name of the destination party|  
|SourceParty|Name of the source party|  
|PIPCode|For example, PIP3A4|  
|PIPVersion|For example, V02.00|  
|MessageContent|Message in binary format|  
|MessageTrackingID|Message tracking ID of the message|  
|PIPInstanceID|PIP instance ID of the process|  
  
## See Also  
 [What BizTalk Accelerator for RosettaNet Adds to BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)   
 [PIP Implementation](../../adapters-and-accelerators/accelerator-rosettanet/pip-implementation.md)
