---
title: "Ambiguous certificate reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7a6a60d-97e6-4c60-86be-83efb4a50f99
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ambiguous certificate reference
## Details  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |       Ambiguous certificate reference; more than one valid certificate found       |
  
## Explanation  
 More than one valid certificate was found.  
  
#### User action  
 Verify only one valid certificate is configured.  
  
## Verify certificate 
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and click **BizTalk Server Administration**.  
  
2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.  
  
3. Locate your application and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Click **Configure**.  
  
8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **General** tab.  
  
9. Click **Edit**.  
  
10. In the **Identity Editor** dialog box, make sure the search criteria in the **Certificate Reference** section is configured properly to indicate only one certificate in the certificate **Store name**.  
  
## Verify a certificate for the WCF-Custom and the WCF-CustomIsolated adapters  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  
  
2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.  
  
3. Locate your application and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Click **Configure**.  
  
8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Behavior** tab.  
  
9. Ensure the search criteria in the **Certificate Reference** section is configured properly to indicate only one certificate in the certificate **Store name**.  
  
10. In the Certificate snap-in, make sure only one certificate is installed for the search criteria you configured to the WCF transport.  
  
## See also
[Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)  
 