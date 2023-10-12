---
description: "Learn more about: Tag Handling in Delimited Records"
title: "Tag Handling in Delimited Records"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Tag Handling in Delimited Records

## Overview
Delimited records can include a well-known sequence of characters, known as a tag, which can be used to disambiguate one type of record from another. This will allow the flat file disassembler to properly identify the appropriate **Record** node in the schema that contains the information required to correctly parse the flat file record.  

 You can use the **Tag Identifier** property to specify the tag within a delimited record. Unlike tags in positional records, tags in delimited records must occur at the beginning of the delimited record and are automatically never included in the data when the record is translated to its equivalent XML format.  

## See Also  
- [Delimited Record Considerations](../core/delimited-record-considerations.md)   
- **Tag Identifier (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
