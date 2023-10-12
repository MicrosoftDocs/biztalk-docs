---
description: "Learn more about: Could not get the database or the server names"
title: "Could not get the database or the server names"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Could not get the database or the server names
## Details  

|    Field        |                     Error Details                                                      |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |                     Could not get the database or the server names                     |

## Explanation  
 This error indicates BizTalk could not read the BizTalkMgmtDb name and Server name from registry. One possible reason for this error is the BizTalk Group is not configured.  

## User Action  
 To resolve this error, configure the BizTalk Group:  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  

3. Right-click **BizTalk Group**.  

4. Click **Properties**.  

5. In the left pane, click **General**.  

6. Verify the **Server** name and **Database** name are correct.
