---
title: "Operations on Tables With BFILE Data Types in Oracle Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "operations, on tables with BFILE data types"
  - "BFILE data type"
  - "BFILE"
ms.assetid: 7937564e-4423-459f-9824-6a27113ebfb3
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on Tables With BFILE Data Types in Oracle Database
The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports the BFILE data type in tables and stored procedures. The following table summarizes the BFILE data type exposed by the adapter based on the operation performed and the LOB artifact (table/procedure) accessed:  
  
|Artifact|Operation|Data type exposed for BFILE col/param|Comments|  
|--------------|---------------|--------------------------------------------|--------------|  
|TABLE|INSERT|String|Represents the logical Oracle directory path to the file to be inserted into the BFILE column<br /><br /> E.g. MYDIR/screen.jpg where MYDIR is a logical directory in Oracle|  
|TABLE|UPDATE|String|Represents the logical Oracle directory path to the file to be updated into the BFILE column|  
|TABLE|SELECT|byte[]|Represents the binary data constituting the BFILE|  
|STORED PROC|IN PARAM|String|Represents the logical Oracle directory path to the file to be inserted into the BFILE column<br /><br /> E.g. MYDIR/screen.jpg where MYDIR is a logical directory in Oracle|  
|STORED PROC|OUT PARAM|String|Represents the logical Oracle directory path to the file to be inserted into the BFILE column<br /><br /> E.g. MYDIR/screen.jpg where MYDIR is a logical directory in Oracle|  
|STORED PROC|INOUT PARAM|Not Supported|-|  
  
 The special operation ReadLOB is also supported on tables with BFILE data type. The UpdateLOB operation is not supported. Adapter clients can alternately use the UPDATE operation.  
  
 For more information about:  
  
- Performing operations on tables containing BFILE data types by using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Run operations on Tables with BFILE Data Types in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md).  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)