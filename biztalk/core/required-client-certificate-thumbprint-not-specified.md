---
description: "Learn more about: Required client certificate thumbprint not specified"
title: "Required client certificate thumbprint not specified"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Required client certificate thumbprint not specified
## Details  
  
| Field | Error Details |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |               Required client certificate thumbprint not specified.                |
  
## Explanation  
 You did not set the Client certificate property required for the security settings of a WCF send port.  
  
## User Action  
 Use the following procedure to configure security settings of a WCF send port.  
  
#### To configure security settings  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  
  
2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  
  
3. Locate your application and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Click **Configure**.  
  
8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Security** tab.  
  
9. Ensure that the **Client certificate** property is configured.  
  
   For additional information on certificates, see the following resource:  
  
-   [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)
