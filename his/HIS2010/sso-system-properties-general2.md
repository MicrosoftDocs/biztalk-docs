---
title: "SSO System Properties: General2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts06.esso.system.properties.general"
ms.assetid: 342dce33-b3c2-49a7-ad0f-2d1545ef9c84
caps.latest.revision: 4
---
# SSO System Properties: General
This screen displays general properties for the overall SSO system.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Master secret server**|The master secret server is the Enterprise Single Sign-On (SSO) server that stores the master secret (encryption key). The master secret server generates the master secret when an SSO Administrator requests it. The master secret server stores the encrypted master secret in the registry. Only SSO Administrators can access the master secret.|  
|**Ticket timeout (in minutes)**|This property specifies the length of time for which a ticket that SSO issues is valid. To satisfy most of the scenarios in an enterprise that use SSO, the default ticket time-out is 2 minutes. The SSO Administrator can change this based on the application requirements.|  
|**Credential cache timeout (in minutes)**|This property specifies the credential cache time-out for all SSO servers. SSO servers cache the credentials after the first lookup. By default, the credential cache time-out is 60 minutes. The SSO Administrator can change this to a suitable value based on the security requirements.|  
  
## See Also  
 [Enterprise Single Sign-On (Configuration)](../HIS2010/enterprise-single-sign-on-configuration-2.md)   
 [Enterprise Single Sign-On System](../HIS2010/enterprise-single-sign-on-system1.md)