---
title: "3270 User Record Format1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eaa425ed-5e07-40da-9529-2ed6ac1aa360
caps.latest.revision: 3
---
# 3270 User Record Format
Two structures make up the 2370 user record:  
  
 [Tecwrksd](../HIS2010/tecwrksd2.md), a logical unit (LU)/session information record, which includes details of a 3270 LU.  
  
 [Tecwrkus](../HIS2010/tecwrkus2.md), a 3270 user record, which includes a number of [Tecwrksd](../HIS2010/tecwrksd2.md) LU/session information records.  
  
 Note that the user record is not a fixed length, because the number of LU/session information records in the remap list is variable. The structures described in the following sections are provided simply as a template to allow you to map to the correct offset in the record.  
  
## In This Section  
  
-   [tecwrksd](../HIS2010/tecwrksd2.md)  
  
-   [tecwrkus](../HIS2010/tecwrkus2.md)