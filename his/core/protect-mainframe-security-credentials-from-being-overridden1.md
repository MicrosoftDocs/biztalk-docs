---
title: "Protect Mainframe Security Credentials from Being Overridden1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51fdedee-23e1-434b-87ae-24007cb3f322
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Protect Mainframe Security Credentials from Being Overridden
To prevent an attacker from gaining control over security credentials used to access a mainframe host, you should do the following:  
  
-   Use host-initiated Single Sign-On (SSO) in conjunction with valid host UID and PWD passed in the initial connection flows.  
  
-   Set the ClientContext to not allow security credentials to be overridden when using the `SelectionHint` property.  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation2.md)   
 [Remote Environment Selection with the SelectionHint Property](../core/remote-environment-selection-with-the-selectionhint-property1.md)   
 [Specifying a Remote Environment Programmatically](../core/specifying-a-remote-environment-programmatically2.md)