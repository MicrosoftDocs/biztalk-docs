---
description: "Learn more about: Unable to access agreement"
title: "Unable to access agreement"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Unable to access agreement
## Details  

| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                              UnableToLocateAS2PartyError                               |
|  Message Text   |            Unable to access agreement. AS2From: {0} AS2To: {1}. Error: {2}             |

## Explanation  
 This error indicates BizTalk Server could not find a party for the given qualifier and value.  

## User Action  
 To resolve this error, create a party alias for the given qualifier:  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and click **Parties**.  

3. Right-click the correct party.  

4. Click **Properties**.  

5. In the [*party name*] **Party Properties** dialog box, enter **EDIINT-AS2 From Value** in the **Name** column.  

6. Enter the party name in the **Value** column.  

7. Click **OK**.
