---
title: "dateTimeMask | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f32c998e-06cc-48e3-9000-77d160739e82
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# dateTimeMask
The dateTimeMask element contains a db2ToSql or sqlToDb2 to indicate the direction, and a sourceFormat and a targetFormat to specify the mapping.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<conversionFormats>  
\<dateTimeMasks>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <conversionFormats>                                <dateTimeMasks>                                        <dateTimeMask>                                        </dateTimeMask>                                </dateTimeMasks>                        </conversionFormats>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The db2ToSql defines the direction from DB2 to SQL Server.|1|  
||The sqlToDb2 defines the direction from SQL Server to DB2.|1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The DRDA Service will process string literal timestamp values within DB2 and SQL Server TIMESTAMP, DATETIME2 (6), CHAR (26), and VARCHAR (26) data types, to convert from DB2 timestamp format to SQL Server datetime2 (6) format, and to convert from SQL Server datetime2 (6) format to DB2 timestamp format. The dateTimeMasks contains one or more dateTimeMask elements to define timestamp-datetime mappings.|