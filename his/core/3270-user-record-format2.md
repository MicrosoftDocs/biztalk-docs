---
title: "3270 User Record Format2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80cee6cd-0323-4be4-829f-641f139127cb
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# 3270 User Record Format
Two structures make up the 2370 user record:  
  
 [Tecwrksd](../core/tecwrksd1.md), a logical unit (LU)/session information record, which includes details of a 3270 LU.  
  
 [Tecwrkus](../core/tecwrkus1.md), a 3270 user record, which includes a number of [Tecwrksd](../core/tecwrksd1.md) LU/session information records.  
  
 Note that the user record is not a fixed length, because the number of LU/session information records in the remap list is variable. The structures described in the following sections are provided simply as a template to allow you to map to the correct offset in the record.  
  
## In This Section  
  
-   [tecwrksd](../core/tecwrksd1.md)  
  
-   [tecwrkus](../core/tecwrkus1.md)