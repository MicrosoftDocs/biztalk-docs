---
description: "Learn more about: Application not found"
title: "Application not found"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Application not found
## Details  

|      Field  |                                        Error Details                                                            |
|-----------------|---------------------------------------------------------------------------------------------------------|
|  Product Name   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]            |
| Product Version |                       [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                        |
|    Event ID     |                                                    0                                                    |
|  Event Source   |                                                    0                                                    |
|    Component    |                                                    0                                                    |
|  Symbolic Name  |                                                    0                                                    |
|  Message Text   | Application "{0}" not found.Verify the application exists in the default BizTalk configuration database |

## Explanation  
 This error indicates BizTalk is using an application that does not exist in the BizTalk databases.  

## User Action  
 Use the following procedure to configure a valid application.  

#### To configure a valid application  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  

2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.  

3. Ensure that the application exists there. If not, select a different valid application.
