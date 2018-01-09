---
title: "WHERE Clause Parsing1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cab40b65-760a-493c-bafc-deface4d0bc2
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# WHERE Clause Parsing
The following describes the parsing rules for a `WHERE` clause for the Managed Provider for Host Files and provides sample parsing statements.  
  
1.  Check whether the token is `KEY` or `POSITION`.  
  
2.  If the token is `KEY`:  
  
    1.  The next token should be an open parenthesis (`(`), followed by the column collection, followed by a close parenthesis (`)`).  
  
    2.  The next token can be `=` or `EQUALS` or `BETWEEN`.  
  
    3.  If the token is `=` or `EQUALS`, then it should be followed by values. Refer to [Value Parsing](../core/value-parsing1.md) for details about the values.  
  
    4.  If the token is `BETWEEN`, then it should be followed by a value, optionally followed by the `INCLUSIVE` or `EXCLUSIVE` keyword. Then it should be followed by `AND`, followed by another value, optionally followed by `INCLUSIVE` or `EXCLUSIVE`.  
  
3.  If the token is `POSITION`:  
  
    1.  The next token can be `=` or `EQUALS` or `BETWEEN`.  
  
    2.  If the token is `=` or `EQUALS`, then it should be followed by values. Refer to [Value Parsing](../core/value-parsing1.md) for details about the values.  
  
    3.  If the token is `BETWEEN`, then it should be followed by a value, optionally followed by the `INCLUSIVE` or `EXCLUSIVE` keyword. Then it should be followed by `AND`, followed by another value, optionally followed by `INCLUSIVE` or `EXCLUSIVE`.  
  
## Example  
 The following is a sample set of parsing statements for the `WHERE` clause for the Managed Provider for Host Files.  
  
```  
WHERE KEY (KEY_COL) = '1290'  
WHERE KEY (KEY_COL) EQUALS '1290'  
WHERE KEY (KEY_COL) BETWEEN  1290 AND 1390  
WHERE KEY (KEY_COL) BETWEEN  1290 INCLUSIVE AND 1390 EXCLUSIVE  
WHERE POSITION = 101  
WHERE POSITION EQUALS 101  
WHERE POSITION BETWEEN 101 AND 201  
WHERE POSITION BETWEEN 101 EXCLUSIVE AND 201 INCLUSIVE  
```  
  
## See Also  
 [SQL Parsing in the Managed Data Provider for Host Files](../core/sql-parsing-in-the-managed-data-provider-for-host-files2.md)