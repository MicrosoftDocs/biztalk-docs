---
title: "conversionFormats | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1658945-94e5-47ed-86dd-f9d9e60a8d05
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# conversionFormats
The conversionFormats element contains dateMasks, timeMasks, and dateTimeMasks for converting to and from DB2 and SQL Server datetime formats.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <conversionFormats>                        </conversionFormats>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The DRDA Service will process string literal date values within DB2 and SQL Server DATE, CHAR (10), and VARCHAR (10) data types, to convert from DB2 date format to SQL Server date format, and to convert from SQL Server date format to DB2 date format. The dateMasks contains one or more dateMask elements to define date mappings.|0 to 1|  
||The DRDA Service will process string literal timestamp values within DB2 and SQL Server TIMESTAMP, DATETIME2 (6), CHAR (26), and VARCHAR (26) data types, to convert from DB2 timestamp format to SQL Server datetime2 (6) format, and to convert from SQL Server datetime2 (6) format to DB2 timestamp format. The dateTimeMasks contains one or more dateTimeMask elements to define timestamp-datetime mappings.|0 to 1|  
||The DRDA Service will process string literal time values within DB2 and SQL Server TIME, CHAR (8), and VARCHAR (8) data types, to convert from DB2 time format to SQL Server time format, and to convert from SQL Server time format to DB2 time format. The timeMasks contains one or more timeMask elements to define time mappings.|0 to 1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The service element defines the configuration for the DrdaService1 service.|