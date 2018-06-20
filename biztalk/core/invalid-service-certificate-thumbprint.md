---
title: "Invalid service certificate thumbprint | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22e7d74e-40ec-4187-9246-bc8da2a9ce86
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invalid service certificate thumbprint
## Details  
  
|                 |                                                                                    |
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