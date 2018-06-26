---
title: "BizTalk message body element encoding is invalid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b407e5c3-4655-4b2f-8ecc-30eb080ec47c
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk message body element encoding is invalid
## Details  
  
|                 |                                                                                                                |
|-----------------|----------------------------------------------------------------------------------------------------------------|
|  Product Name   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]               |
| Product Version |                           [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                           |
|    Event ID     |                                                       0                                                        |
|  Event Source   |                                                       0                                                        |
|    Component    |                                                       0                                                        |
|  Symbolic Name  |                                                       0                                                        |
|  Message Text   | BizTalk message body element encoding "{0}" is invalid. Expected encoding: "xml", "base64", "hex", or "string" |
  
## Explanation  
 This error indicates the use of the BizTalk body template option for the outgoing messages; however, the encoding type specified for the BizTalk body is invalid.  
  
## User Action  
 Use the following procedure to configure the encoding type.  
  
#### To configure the encoding type  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  
  
2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  
  
3. Locate your application and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Click **Configure**.  
  
8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Messages** tab.  
  
9. In the **Outbound WCF message body** section, click the **Template – Content specified by template** radio button. In the **XML** text box, the format of the BizTalk body should be   
    \<**bts-msg-body xmlns="<http://www.microsoft.com/schemas/bts2007>" encoding="[xml&#124;base64&#124;hex&#124;string]"/**\>  (valid values, which are case-sensitive, for encoding are xml&#124;base64&#124;hex&#124;string)