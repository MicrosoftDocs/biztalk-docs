---
description: "Learn more about: dateMask"
title: "dateMask"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# dateMask
The dateMask element contains a db2ToSql or sqlToDb2 to indicate the direction, and a sourceFormat and a targetFormat to specify the mapping.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<conversionFormats>  
\<dateMasks>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <conversionFormats>                                <dateMasks>                                        <dateMask>                                        </dateMask>                                </dateMasks>                        </conversionFormats>                </service>        </services></hostIntegration.drdaAs.drdaService>  
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
||The DRDA Service will process string literal date values within DB2 and SQL Server DATE, CHAR (10), and VARCHAR (10) data types, to convert from DB2 date format to SQL Server date format, and to convert from SQL Server date format to DB2 date format. The dateMasks contains one or more dateMask elements to define date mappings.|
