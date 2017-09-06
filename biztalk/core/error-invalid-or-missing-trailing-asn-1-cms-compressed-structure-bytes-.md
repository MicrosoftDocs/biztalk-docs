---
title: "Invalid or missing trailing ASN.1 CMS compressed structure bytes during decompression processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b73ce58-d827-4ffc-b2d7-78836298efc8
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invalid or missing trailing ASN.1 CMS compressed structure bytes during decompression processing
## Details  
  
|||  
|-|-|  
|Product Name|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Product Version|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|Event ID|-|  
|Event Source|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Component|AS2 Engine|  
|Symbolic Name|-|  
|Message Text|Invalid or missing trailing ASN.1 CMS compressed structure bytes during decompression processing|  
  
## Explanation  
 This error refers to the ASN.1 structure of the compressed data. The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.  
  
## User Action  
 Review the structure of the compressed data and check for tampering with the message.