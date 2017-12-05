---
title: "Configuration of Enterprise Single Sign-On1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "config.wiz.sso"
ms.assetid: e19d8cc2-5b9c-4c2d-8a64-52d08cc04759
caps.latest.revision: 2
---
# Configuration of Enterprise Single Sign-On
Select **Enable Enterprise Single Sign-On** to make configuration changes on this page.  
  
 Select **Create a new SSO system** if this is the first SSO server you are configuring in your SSO system. This also creates and configures the SSO Credential database. You must also back up the secret on this secret server. You should configure the master secret server as a stand-alone server. You must be an SSO administrator while performing this configuration task. Only one master secret server can be associated with one SSO group. Associating two master secret servers to the same SSO group is not supported. Select **Join an existing SSO system** to connect to an existing SSO system.  
  
## UIElement List  
 **Data stores**  
 The Data stores list provides an editable view of the data stores used for the SSO database.  
  
 **Windows service**  
 The Windows service list provides an editable view of the account used to run the Enterprise Single Sign-On service.  
  
 **Windows accounts**  
 The Windows accounts list provides an editable view of the SSO Administrators and SSO Affiliate Administrators Windows groups.  
  
## See Also  
 [Configuration Wizard Help](../core/configuration-wizard-help1.md)