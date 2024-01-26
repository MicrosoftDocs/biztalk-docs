---
description: "Learn more about: INSERT Statement"
title: "INSERT Statement2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# INSERT Statement
The following describes the syntax of the `INSERT` statement for the Managed Provider for Host Files, and provides sample `INSERT` statements.  
  
## Syntax  
 INSERT INTO Filename VALUES (\<Values>)  
  
 INSERT INTO Filename AS \<AssemblyName.SchemaName> VALUES (\<Values>)  
  
 INSERT INTO Filename (\<Column Collection>) VALUES (\<Values>)  
  
 INSERT INTO Filename AS \<AssemblyName.SchemaName> (\<Column Collection>) VALUES (\<Values>)  
  
## Example  
 The following are sample `INSERT` statements for the Managed Provider for Host Files.  
  
```  
INSERT INTO Filename (COL1, COL2…) VALUES(value1, Value2…)  
INSERT INTO Filename AS Library_VSAM.NUMBERS  (OUT1_CHAR1, UNION1, UNION2, UNION3, UNION4, UNION5, UNION6, OUT1_DECIMAL, OUT1_DOUBLE, OUT1_SINGLE) VALUES  ("RECORD", {1234}, {276578853}, {1234}, {271111111}, {-1234}, {-135363175}, 100, 100, 100)  
```  
