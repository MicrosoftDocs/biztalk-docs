---
title: "Data and Time Format Conversions | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02540779-14a9-4de8-8d7f-780f3f034a63
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data and Time Format Conversions
The DRDA Service converts to and from DB2 and SQL Server date time formats based on a defined set of format masks in the MsDrdaService.exe.config file—to support interoperability between DB2, SQL Server, ISO and string literal datetime values. See the Operations book for more information on date masks, time masks, and datetime masks.  
  
## DB2 TIME and TIMESTAMP with Hour 24  
 IBM DB2 TIME and TIMESTAMP can contain an Hour 24 value that is out of range of Microsoft SQL Server TIME, DATETIME, and DATETIME2 data types.  
  
 IBM DB2 supports a TIME value range from 00.00.00 to 24.00.00, and TIMESTAMP value range from 0001-01-01-00.00.00.000000 to 9999-12-31-24.00.00.000000.  
  
 SQL Server supports a TIME value range from 00:00:00.0000000 to 23:59:59.9999999, and DATETIME2 value range from 01-01-01 00:00:00 to 9999-12-31 23:59:59.9999999.  
  
 The DRDA Service will transform DB2 TIME and TIMESTAMP values with hour 24 into SQL Server TIME, DATETIME, and DATETIME2 values with hour 00:00:00 of the next day. For example, the DRDA Service will transform the DB2 TIME value ’24:00:00’ into the SQL Server TIME value ’00:00:00’). For example, the DRDA Service will transform the DB2 DATETIME value '2011-12-31-24.00.00.000000' into the SQL Server DATETIME/DATETIME2 value '2012-01-01-00.00.00.000000'.