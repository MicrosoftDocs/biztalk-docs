---
title: "How to Use the ENTSSO Management Agent | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 536cbfa2-741f-4d43-95b6-876a6b172c5b
caps.latest.revision: 6
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Use the ENTSSO Management Agent
This version of Enterprise Single Sign-On (SSO) contains a Management Agent (MA) for Microsoft Forefront Identity Manager, which integrates Enterprise SSO with the account synchronization capabilities of FIM 2007. This enables an FIM administrator to manage SSO mappings in the SSO Credential Database.  
  
 In Enterprise SSO, mappings are created between Windows Domain accounts (*domainname\username*) and external credentials. If you have an Active Directory Management Agent, and the Management Agent for the external Data Source (example: RACF MA), you can use the Enterprise SSO MA (ENTSSO MA) to manage mappings in the SSO Credential Database. ENTSSO MA is a *Call-Based Export* Management Agent only.  
  
 You configure the Management Agent in three separate parts:  
  
- A configuration file (ENTSSO.xml)  
  
- The ENTSSO user interface  
  
  The topics in this section describe the configuration process.  
  
## In This Section  
 [How to Configure the XML File](../esso/how-to-configure-the-xml-file.md)  
  
 [How to Configure ENTSSO for ILM Password Sync](../esso/how-to-configure-entsso-for-ilm-password-sync.md)  
  
## See Also  
 [Enterprise Single Sign-On](../esso/enterprise-single-sign-on1.md)