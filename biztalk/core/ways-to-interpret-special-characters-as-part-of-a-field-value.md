---
description: "Learn more about: Ways to Interpret Special Characters as Part of a Field Value"
title: "Ways to Interpret Special Characters as Part of a Field Value | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e19a202-4e4d-42e0-ba1e-fddc52792b21
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ways to Interpret Special Characters as Part of a Field Value
Fields in both positional and delimited records can contain special characters of different types, such as pad, wrap, and escape characters. Delimited records can also contain one or more different delimiter characters that are used to separate the fields within a record and one record from another record. Sometimes these special characters are part of the data itself, and are not meant to be interpreted as special in those cases.  
  
 The flat file schemas used by Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] support two different techniques for flagging occurrences of otherwise special characters as simply part of the data contained by a field. These two techniques employ escape characters and wrap characters, respectively.  
  
## In This Section  
  
-   [Escape Characters](../core/escape-characters.md)  
  
-   [Wrap Characters](../core/wrap-characters.md)
