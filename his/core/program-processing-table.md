---
title: "Program Processing Table1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d6b595d-b2ad-4a4c-97e5-c6209ffa7200
caps.latest.revision: 3
---
# Program Processing Table
The Program Processing Table (PPT) defines the load module characteristics to CICS.  
  
 Each load module is defined using the DFHPPT definition, which includes the name of the load module (the PROGRAM field), and the language in which the module has been written. Examples are PL/I, Assembler, or COBOL (the PGMLANG field).  
  
### Sample CICS program processing table entries  
  
|Definition|Program name|Language|  
|----------------|------------------|--------------|  
|DFHPPT TYPE=ENTRY|PROGRAM=TRAN0000|PGMLANG=PL/I|  
|DFHPPT TYPE=ENTRY|PROGRAM=TRAN0001|PGMLANG=PL/I|  
|DFHPPT TYPE=ENTRY|PROGRAM=TRAN0002|PGMLANG=PL/I|  
|DFHPPT TYPE=ENTRY|PROGRAM=TRAN0003|PGMLANG=PL/I|  
  
## See Also  
 [CICS Tables](../core/cics-tables.md)