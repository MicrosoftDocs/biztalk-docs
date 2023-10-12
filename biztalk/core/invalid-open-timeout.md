---
description: "Learn more about: Invalid open timeout"
title: "Invalid open timeout"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid open timeout
## Details  

| Field | Error Details |
|-----------------|-----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]    |
| Product Version |               [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                |
|    Event ID     |                                            0                                            |
|  Event Source   |                                            0                                            |
|    Component    |                                            0                                            |
|  Symbolic Name  |                                            0                                            |
|  Message Text   | Invalid open timeout. Valid range: 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds. |

## Explanation  

## User Action  
 Use the following procedure to configure the timeout range.  

#### To configure the timeout range  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  

2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  

3. Locate your application and then locate your transport.  

4. Right-click the transport name.  

5. Click **Properties**.  

6. In the port **Type** list, select the correct port.  

7. Click **Configure**.  

8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.  

9. Ensure the timeout range is valid. Acceptable values are 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds.
