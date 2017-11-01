---
title: "Protect Mainframe Security Credentials from Being Overridden1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51fdedee-23e1-434b-87ae-24007cb3f322
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Protect Mainframe Security Credentials from Being Overridden
To prevent an attacker from gaining control over security credentials used to access a mainframe host, you should do the following:  
  
-   Use host-initiated Single Sign-On (SSO) in conjunction with valid host UID and PWD passed in the initial connection flows.  
  
-   Set the ClientContext to not allow security credentials to be overridden when using the `SelectionHint` property.  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation.md)   
 [Remote Environment Selection with the SelectionHint Property](../Topic/Remote%20Environment%20Selection%20with%20the%20SelectionHint%20Property1.md)   
 [Specifying a Remote Environment Programmatically](../Topic/Specifying%20a%20Remote%20Environment%20Programmatically2.md)