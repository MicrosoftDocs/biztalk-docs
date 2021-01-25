---
description: "Learn more about: CIDX Messaging Standards"
title: "CIDX Messaging Standards | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CIDX, RosettaNet"
  - "RosettaNet, CIDX"
ms.assetid: 6f70fa56-1fc3-4016-ac9e-6af18026292a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# CIDX Messaging Standards
CIDX (Chemical Industry Data Exchange) operates as a standards organization that supports and maintains the Chem eStandards for standardized message exchange. Companies in the chemical industry use these standards for their industry-specific messaging needs.  
  
 CIDX has adopted the RosettaNet Implementation Framework (RNIF) at the messaging layer to enable the exchange of XML documents. CIDX has not adopted the public-process layer of the RNIF standards.  
  
 Chem eStandards define XML document type definitions (DTDs) that describe the service content of a message that systems exchange. The message is the same as an RNIF 1.1 RosettaNet object in structure, with differences in the service content and some header values. When there is a match between CIDX standards and RosettaNet messages, the CIDX standard adopts RosettaNet element names and data structures.  
  
 CIDX has traditionally used electronic document interchange (EDI) for message exchange, but has formed a new set of documents based on XML technologies. Chem eStandards provide XML replicas of EDI messages.  
  
 Chem eStandards create individual messages for every business transaction. Chem eStandards use two types of message responses: technical responses and transaction responses. For secure and reliable messaging, Chem eStandards only use Notification type processes of RNIF 1.1. Chem eStandards do not use Partner Interface Process (PIP) 0A1.  
  
## CIDX and RosettaNet Differences  
 The following table shows some of the differences between RosettaNet and CIDX.  
  
|RosettaNet implementation|CIDX implementation|  
|-------------------------------|-------------------------|  
|RosettaNet uses the "Application/x-RosettaNet" as the Multipurpose Internet Mail Extensions (MIME) type.|CIDX uses "Application/x-ChemXML" as the MIME type.|  
|For RosettaNet headers, RosettaNet uses GlobalAdministeringAuthorityCode = RosettaNet|CIDX uses GlobalAdministeringAuthorityCode = CIDX|  
|RosettaNet supports single-action and double-action messages.|CIDX supports only single-action messages.|  
|RosettaNet supports PIP 0A1 (Notification of Failure).|CIDX does not support PIP 0A1.|  
|RosettaNet messages can be of Transaction or Notification type.|All CIDX messages are of the Notification type.|  
|In RosettaNet, you must derive PIP Configuration Settings from the PIP specifications.|In CIDX, you must derive PIP Configuration Settings from the CIDX Chem eStandards specifications.|  
  
## See Also  
 [RosettaNet and CIDX Messaging Standards](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md)   
 [RNIF Standard](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md)   
 [RosettaNet PIPs](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)   
 [CIDX Support](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md)
