---
title: "Required affiliate application name not specified | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3e82a39-b052-4702-bfe2-700756a0ee6a
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Required affiliate application name not specified
## Details  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                 Required affiliate application name not specified                  |
  
## Explanation  
 **Use Single Sign-On** option has been selected but the affiliate application name has not been specified.  
  
## User Action  
 Use the following procedure to configure the affiliate application name.  
  
#### To configure the affiliate application name  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  
  
2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **BizTalk Applications**.  
  
3. Locate your application and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select **WCF-Custom**.  
  
7. Click **Configure**.  
  
8. In the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab.  
  
9. In the **User name credentials** section, specify a value for **Affiliate application**.  
  
   For more information about creating an SSO affiliate application, see [http://go.microsoft.com/fwlink/?LinkId=94347](http://go.microsoft.com/fwlink/?LinkId=94347)