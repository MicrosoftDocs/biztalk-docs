---
title: "Sync Point Support Architecture2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19503eca-9c85-4ae3-b43e-f4079429139e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Sync Point Support Architecture
The Sync Point support provided by Host Integration Server assumes a particular implementation architecture by the vendor, as follows:  
  
- The vendor provides a communication interface to its own clients requiring Sync Point Services (SPS).  
  
- The vendor API maps its communication and Sync Point requests to the Host Integration Server APPC API.  
  
- The vendor provides a single Microsoft Windows process, the Transaction Monitor, that is responsible for:  
  
  - Issuing all APPC verbs.  
  
  - Implementing the architected Resynchronization TP.  
  
  - Implementing the architected Conversation-Protected Resource Manager (C-PRM) component of the logical unit (LU).  
  
  - Implementing the architected SPS component of the LU.  
  
    The Transaction Monitor must reside on the same computer as the Host Integration Server containing the LUs for which it is providing Sync Point services. Both incoming and outgoing Sync Point conversations for this Transaction Monitor will be routed through this Host Integration Server server only.  
  
  Detailed descriptions of the three architected Sync Point components can be found in *SNA LU6.2 Reference: Peer Protocols* published by IBM.