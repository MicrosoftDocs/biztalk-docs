---
description: "Learn more about: Protect Mainframe Security Credentials from Being Overridden"
title: "Protect Mainframe Security Credentials from Being Overridden1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Protect Mainframe Security Credentials from Being Overridden
To prevent an attacker from gaining control over security credentials used to access a mainframe host, you should do the following:  
  
-   Use host-initiated Single Sign-On (SSO) in conjunction with valid host UID and PWD passed in the initial connection flows.  
  
-   Set the ClientContext to not allow security credentials to be overridden when using the `SelectionHint` property.  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation2.md)   
 [Remote Environment Selection with the SelectionHint Property](./remote-environment-selection-with-the-selectionhint-property2.md)   
 [Specifying a Remote Environment Programmatically](./specifying-a-remote-environment-programmatically1.md)
