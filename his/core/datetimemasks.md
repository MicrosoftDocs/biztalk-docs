---
description: "Learn more about: dateTimeMasks"
title: "dateTimeMasks"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# dateTimeMasks
The DRDA Service will process string literal timestamp values within DB2 and SQL Server TIMESTAMP, DATETIME2 (6), CHAR (26), and VARCHAR (26) data types, to convert from DB2 timestamp format to SQL Server datetime2 (6) format, and to convert from SQL Server datetime2 (6) format to DB2 timestamp format. The dateTimeMasks contains one or more dateTimeMask elements to define timestamp-datetime mappings.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<conversionFormats>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <conversionFormats>                                <dateTimeMasks>                                </dateTimeMasks>                        </conversionFormats>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The dateTimeMask element contains a db2ToSql or sqlToDb2 to indicate the direction, and a sourceFormat and a targetFormat to specify the mapping.|1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The conversionFormats element contains dateMasks, timeMasks, and dateTimeMasks for converting to and from DB2 and SQL Server datetime formats.|
