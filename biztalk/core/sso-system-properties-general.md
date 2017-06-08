---
title: "SSO System Properties: General | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.esso.system.properties.general"
ms.assetid: 5f61cfef-5afa-4a1a-b2ab-959c02d028f2
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SSO System Properties: General
This screen displays general properties for the overall SSO system.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Master secret server**|The master secret server is the Enterprise Single Sign-On (SSO) server that stores the master secret (encryption key). The master secret server generates the master secret when an SSO Administrator requests it. The master secret server stores the encrypted master secret in the registry. Only SSO Administrators can access the master secret.|  
|**Ticket timeout (in minutes)**|This property specifies the length of time for which a ticket that SSO issues is valid. To satisfy most of the scenarios in an enterprise that use SSO, the default ticket time-out is 2 minutes. The SSO Administrator can change this based on the application requirements.|  
|**Credential cache timeout (in minutes)**|This property specifies the credential cache time-out for all SSO servers. SSO servers cache the credentials after the first lookup. By default, the credential cache time-out is 60 minutes. The SSO Administrator can change this to a suitable value based on the security requirements.|  
  
## See Also  
 [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)