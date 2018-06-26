---
title: "How to Use the ENTSSO Management Agent | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c89b494-db12-4d2a-a030-6acd34489cab
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Use the ENTSSO Management Agent
This version of Enterprise Single Sign-On (SSO) contains a Management Agent (MA) for Microsoft Identity Integration Server (MIIS), which integrates Enterprise SSO with the account synchronization capabilities of MIIS. This enables an MIIS administrator to manage SSO mappings in the SSO Database.  
  
 In Enterprise SSO, mappings are created between Windows Domain accounts (*domainname\username*) and external credentials. If you have an Active Directory Management Agent, and the Management Agent for the external Data Source (example: RACF MA), you can use the Enterprise SSO MA (ENTSSO MA) to manage mappings in the SSO Database. ENTSSO MA is a *Call-Based Export* Management Agent only.  
  
 You configure the Management Agent in three separate parts:  
  
- A configuration file (ENTSSO.xml)  
  
- The MIIS user interface  
  
- The ENTSSO user interface  
  
  The topics in this section describe the configuration process.  
  
## In This Section  
  
-   [Configuring the XML File](../core/configuring-the-xml-file.md)  
  
-   [How to Configure MIIS for ENTSSO MA](../core/how-to-configure-miis-for-entsso-ma.md)  
  
-   [How to Configure ENTSSO for MIIS Password Sync](../core/how-to-configure-entsso-for-miis-password-sync.md)