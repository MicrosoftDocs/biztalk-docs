---
description: "Learn more about: Invalid service certificate thumbprint"
title: "Invalid service certificate thumbprint"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid service certificate thumbprint
## Details  
  
| Field | Error Details |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |       Invalid service certificate thumbprint; expected 40 hexadecimal digits       |
  
## Explanation  
 An invalid service certificate thumbprint was specified.  
  
## User Action  
 In the code configuring the WCF port, the service certificate property of the user interface expects a hexadecimal 40-digit value. Example: 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39  
  
 For additional information on certificates, see the following resource:  
  
-   [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)
