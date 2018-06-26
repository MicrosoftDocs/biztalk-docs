---
title: "Invalid time to live timeout | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2ddb6de-8c3b-4dee-a984-980e1caea95e
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invalid time to live timeout
## Details  

|                 |                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------|
|  Product Name   |       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]       |
| Product Version |                   [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                   |
|    Event ID     |                                               0                                                |
|  Event Source   |                                               0                                                |
|    Component    |                                               0                                                |
|  Symbolic Name  |                                               0                                                |
|  Message Text   | Invalid time to live timeout. Valid range: 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds |

## Explanation  

## User Action  
 Use the following procedure to configure the timeout range.  

#### To configure the timeout range  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  

2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  

3. Locate your application and then locate your transport.  

4. Right-click the transport name.  

5. Click **Properties**.  

6. In the port **Type** list, select **WCF-NetMsmq**.  

7. Click **Configure**.  

8. In the **WCF-NetMsmq Transport Properties** dialog box, click the **Binding** tab.  

9. In the **Queue Settings** section, ensure the **Message time to live (dd:hh:mm:ss)** range is valid. Acceptable values are 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds.
