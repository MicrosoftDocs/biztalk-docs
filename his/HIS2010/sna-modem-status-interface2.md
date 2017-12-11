---
title: "SNA Modem Status Interface2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b2f6e68-c0d9-4ee5-a6e7-d634e0ab58b9
caps.latest.revision: 3
---
# SNA Modem Status Interface
This section describes the interface to the modem status used by Synchronous Data Link Control (SDLC) and X.25 SNALinks that [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] supplies. This interface provides a set of simulated modem lights to show modem status. The modem status interface is intended primarily for the Microgate cards with internal modems, but can be used with any SDLC or X.25 link service to show the modem status.  
  
 This interface is intended primarily for independent hardware vendors (IHV) who want to provide drivers for their own dumb cards that are directly compatible with SDLC and X.25 SNALinks that Host Integration Server provides. It can also be used by IHVs who intend to write their own SNALinks but who want to ensure that their drivers conform to the standard Host Integration Server model.  
  
## In This Section  
 [SNA Device Driver Interface to Modem Status](../HIS2010/sna-device-driver-interface-to-modem-status1.md)  
  
 [Supporting Modem Status in an SNA Link Service](../HIS2010/supporting-modem-status-in-an-sna-link-service2.md)  
  
 [Modem API Summary](../HIS2010/modem-api-summary1.md)  
  
 [DevIoctl Definitions to Support SNA Modem Status](../HIS2010/devioctl-definitions-to-support-sna-modem-status2.md)