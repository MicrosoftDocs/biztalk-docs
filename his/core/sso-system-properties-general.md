---
title: "SSO System Properties: General1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f928899-2001-40cd-a49f-2b60fcafef52
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# SSO System Properties: General
This screen displays general properties for the overall SSO system.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Master secret server**|The master secret server is the Enterprise Single Sign-On (SSO) server that stores the master secret (encryption key). The master secret server generates the master secret when an SSO Administrator requests it. The master secret server stores the encrypted master secret in the registry. Only SSO Administrators can access the master secret.|  
|**Ticket timeout (in minutes)**|This property specifies the length of time for which a ticket that SSO issues is valid. To satisfy most of the scenarios in an enterprise that use SSO, the default ticket time-out is 2 minutes. The SSO Administrator can change this based on the application requirements.|  
|**Credential cache timeout (in minutes)**|This property specifies the credential cache time-out for all SSO servers. SSO servers cache the credentials after the first lookup. By default, the credential cache time-out is 60 minutes. The SSO Administrator can change this to a suitable value based on the security requirements.|  
  
## See Also  
 [Enterprise Single Sign-On (Configuration)](../core/enterprise-single-sign-on-configuration.md)   
 [Enterprise Single Sign-On System](../core/enterprise-single-sign-on-system.md)