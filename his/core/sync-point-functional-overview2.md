---
title: "Sync Point Functional Overview2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 46064ad1-d4ae-4c43-b146-077e893726d3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Sync Point Functional Overview
The Sync Point support additions to Host Integration Server allow vendors to provide Sync Point services over LU 6.2 conversations provided by the LU 6.2 protocol stack in Host Integration Server. These additions do not implement the architected Sync Point components and TPs necessary for a complete Sync Point implementation. In particular, the following Sync Point components are not implemented, and must be provided by the vendor.  
  
- Sync Point Services (SPS)  
  
- Conversation-Protected Resource Manager (C-PRM)  
  
- Resynchronization TP  
  
  These vendor-supplied components and applications are expected to implement the **SYNCPT** and **BACKOUT** verbs used for Sync Point services. The **SYNCPT** verb is used to synchronize transactions. The **BACKOUT** verb is used to back out of a transaction.  
  
  SPS, C-PRM, and the Resynchronization TP are specific components of the SNA Sync Point architecture described in *SNA LU6.2 Reference: Peer Protocols* published by IBM.  
  
  Host Integration Server has been modified to add the features necessary to support these components, namely:  
  
- Additions to the existing APPC API to support implementation of Sync Point verbs.  
  
- Accounting support for Sync Point protocols.  
  
- Modifications to invokable transaction program (TP) initiation.  
  
  Changes to the APPC basic and mapped conversation APPC APIs are made so as to ensure backward compatibility with existing APPC applications that adhere strictly to the API.  
  
> [!NOTE]
>  Applications must zero all reserved verb control block (VCB) members before issuing an APPC verb. If this is not done, the application may inadvertently invoke one of the new APPC features.