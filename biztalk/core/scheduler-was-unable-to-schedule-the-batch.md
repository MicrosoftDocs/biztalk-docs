---
description: "Learn more about: Scheduler was unable to schedule the batch"
title: "Scheduler was unable to schedule the batch"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Scheduler was unable to schedule the batch
## Details  

| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                    Batching Engine                                     |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |                       Scheduler was unable to schedule the batch                       |

## Explanation  
 This error indicates the scheduler could not determine the next occurrence of a batch release.  

## User Action  
 To resolve this error, make sure the batch release schedule is valid:  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and click **Parties**.  

3. Right-click the correct party.  

4. Click **Properties**.  

5. In the [*party name*] **Party Properties** dialog box, in the left pane, click **Send Ports**.  

6. Enter the Send port name in the **Send Ports** list.  

7. Click **OK**.
