---
title: "Structural error encountered during serialization of an interchange XML message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97939bfd-d1ee-455a-9952-4f25db020e7c
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Structural error encountered during serialization of an interchange XML message
## Details  

|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                  InvalidXmlNodeFound                                   |
|  Message Text   |    Structural error encountered during serialization of an Interchange Xml message     |

## Explanation  
 This error indicates that a structural error was encountered during serialization of an interchange XML message. BTS was looking for an XML StartElement or EndElement but instead a different XML node type was encountered.  

## User Action  
 To resolve this error, make sure the message structure is correct, and try again:  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and click **BizTalk Group**.  

3. In the right pane, click the **Group Hub** tab.  

4. Click **Suspended Service instances**.  

5. Double-click the message.  

6. In the **Service Details** window, click the **Messages** tab.  

7. Double-click the message again.  

8. In the left pane, click **Message Parts / Body**.  

9. Determine if the message structure is correct.
