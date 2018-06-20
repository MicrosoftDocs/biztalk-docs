---
title: "Operations on Functions and Procedures with RECORD Types1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: afc1c84f-2e36-493c-9ea8-4bc2248331db
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on Functions and Procedures with RECORD Types
Oracle RECORD types are used to represent hierarchical information in parameters passed to PL/SQL functions and procedures. The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces RECORD types as complex XML types. 

## Supported RECORD types
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] supports the following kinds of RECORD types:  
  
- RECORD types that are declared as TABLE%ROWTYPE parameters in stored procedures and functions.  
  
- RECORD types that are declared as TYPE of RECORD parameters in PL/SQL packages. For example, TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));  
  
- RECORD types that contain nested records.  
  
- RECORD types that appear as IN, OUT, or IN OUT parameters to procedures or functions.  
  
- RECORD types that are RETURN values of functions.  
  
  > [!NOTE]
  >  The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support BFILE types as RECORD members.  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)