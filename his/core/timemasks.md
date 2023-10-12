---
description: "Learn more about: timeMasks"
title: "timeMasks"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# timeMasks
The DRDA Service will process string literal time values within DB2 and SQL Server TIME, CHAR (8), and VARCHAR (8) data types, to convert from DB2 time format to SQL Server time format, and to convert from SQL Server time format to DB2 time format. The timeMasks contains one or more timeMask elements to define time mappings.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<conversionFormats>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <conversionFormats>                                <timeMasks>                                </timeMasks>                        </conversionFormats>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The timeMask element contains a db2ToSql or sqlToDb2 to indicate the direction, and a sourceFormat and a targetFormat to specify the mapping.|1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The conversionFormats element contains dateMasks, timeMasks, and dateTimeMasks for converting to and from DB2 and SQL Server datetime formats.|
