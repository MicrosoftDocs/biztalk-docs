---
title: "Certificate not found | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 629b199f-1884-4e88-beaa-a2e5c5e792e9
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Certificate not found
## Details  
  
|||  
|-|-|  
|Product Name|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Product Version|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|Event ID|0|  
|Event Source|0|  
|Component|0|  
|Symbolic Name|0|  
|Message Text|Certificate not found.|  
  
## Explanation  
 A certificate could not be found for the given search criteria.  
  
## User Action  
 Use the following procedures to verify search criteria for certificates.  
  
#### To verify search criteria  
  
1.  Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  
  
2.  In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  
  
3.  Locate your application and then locate your transport.  
  
4.  Right-click the transport name.  
  
5.  Click **Properties**.  
  
6.  In the port **Type** list, select the correct port.  
  
7.  Click **Configure**.  
  
8.  In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.  
  
9. Click **Edit**.  
  
10. In the **Identity Editor** dialog box, make sure that the search criteria in the **Certificate Reference** section is configured properly to indicate valid certificates.  
  
 For the WCF-Custom and the WCF-CustomIsolated adapters, ensure that the search criteria in the **Certificate Reference** section is configured properly to indicate a valid certificate in the certificate **Store name**.  
  
#### To verify search criteria for standard WCF adapters  
  
1.  Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  
  
2.  In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.  
  
3.  Locate your application and then locate your transport.  
  
4.  Right-click the transport name.  
  
5.  Click **Properties**.  
  
6.  In the port **Type** list, select the correct port.  
  
7.  Click **Configure**.  
  
8.  In the **WCF [***transport type***] Transport Properties** dialog box, click the **Security** tab.  
  
9. Ensure that the **Thumbprint** properties for the service and client certificates indicate valid certificates in certificate stores.  
  
10. In the Certificate snap-in, make sure that valid certificates are installed for the WCF transport.  
  
 For additional information on certificates, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)  
  
-   [WCF Adapters UI Help](../core/wcf-adapters-ui-help.md)