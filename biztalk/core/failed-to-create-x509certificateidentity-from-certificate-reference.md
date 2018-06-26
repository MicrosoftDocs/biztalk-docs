---
title: "Failed to create X509CertificateIdentity from certificate reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3acee8e-c035-4e58-8bfc-397885b4d185
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Failed to create X509CertificateIdentity from certificate reference
## Details  

|                 |                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                             |
| Product Version |                                         [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                         |
|    Event ID     |                                                                     0                                                                      |
|  Event Source   |                                                                     0                                                                      |
|    Component    |                                                                     0                                                                      |
|  Symbolic Name  |                                                                     0                                                                      |
|  Message Text   | Failed to create X509CertificateIdentity from certificate reference. (StoreName={0}, StoreLocation={1}, X509FindType={2}, FindValue="{3}") |

## Explanation  
 This error indicates the adapter failed to create the X509Certificate specified in the endpoint identity configuration.  

## User Action  
 Use the following procedure to verify the certificate reference settings.  

#### To configure the certificate reference settings  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  

2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  

3. Locate your application and then locate your transport.  

4. Right-click the transport name.  

5. Click **Properties**.  

6. In the port **Type** list, select the correct port.  

7. Click **Configure**.  

8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **General** tab.  

9. In the **Endpoint Identity** section, click **Edit.**  

10. In the **Identity Editor** dialog box, ensure that the **Certificate Reference** settings are valid.
