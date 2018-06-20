---
title: "Decompression failed while processing a compressed AS2 message. | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5246ee97-cc60-4878-9447-de870c0f4c34
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Decompression failed while processing a compressed AS2 message.
## Details  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       AS2 Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |       Decompression failed while processing a compressed AS2 message. Error: {0}       |
  
## Explanation  
 This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not decompress the AS2 message.  
  
## User Action  
 To resolve this error, do one of the following:  
  
-   Verify that the compression wrapper in the AS2 message is valid.  
  
-   Verify that decompression is enabled for BizTalk Server by verifying that the "Message should be compressed" property is checked on the Party as AS2 Message Sender page of the AS2 Properties dialog box (if the Override inbound message properties property is checked).  
  
-   Use the error description provided in the error message text to identify the specific issue.