---
title: "Nested Positional and Delimited Records | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1688f04-d3c7-492c-82f7-a734bec0e409
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Nested Positional and Delimited Records
In the flat file formats supported by Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], some combinations of positional and delimited records are allowed and others are disallowed. The following combinations are allowed:  
  
- Flat files in which delimiters are used to determine the boundaries between all records and their subordinate records from each other, and in which (possibly different) delimiters are used to separate the fields within those records.  
  
- Flat files in which the boundaries between all records, their subordinate records, and their fields are determined based on their position within the file according to predefined record and field lengths.  
  
- Flat files in which delimiters are used to determine the boundaries between at least the outermost set of records in the file, and in which a mix of delimited and positional subordinate records are used. Boundaries between the fields within a delimited or positional subordinate record are determined using either delimiters or fixed field lengths, respectively. The subordinate records of a positional (subordinate) record must also be positional; in other words, once a portion of the file switches from delimited to positional records, that entire subordinate portion of the file must be positional.  
  
  Due to the parsing ambiguities that would result, positional records, wherever they occur, are prohibited from containing delimited subordinate records.  
  
## See Also  
 [Considerations When Creating Flat File Message Schemas](../core/considerations-when-creating-flat-file-message-schemas.md)