---
description: "Learn about the sqlToDb2 element that defines the direction from SQL Server to DB2."
title: "sqlToDb23"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# sqlToDb2

The sqlToDb2 defines the direction from SQL Server to DB2.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<conversionFormats>  
\<dateTimeMasks>  
\<dateTimeMask>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <conversionFormats>                                <dateTimeMasks>                                        <dateTimeMask>                                                <sqlToDb2>                                                </sqlToDb2>                                        </dateTimeMask>                                </dateTimeMasks>                        </conversionFormats>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements
  
The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|targetFormat|drdaas:TimeStampFormats||true|n/a|  
  
### Child Elements
  
None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The dateTimeMask element contains a db2ToSql or sqlToDb2 to indicate the direction, and a sourceFormat and a targetFormat to specify the mapping.|
