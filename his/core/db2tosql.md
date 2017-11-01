---
title: "db2ToSql3 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 389ec810-511d-4f6b-ae52-1aa221b2a8a2
caps.latest.revision: 2
ms.author: "dwrede"
---
# db2ToSql
The db2ToSql defines the direction from DB2 to SQL Server.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<conversionFormats>  
\<dateMasks>  
\<dateMask>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <conversionFormats>                                <dateMasks>                                        <dateMask>                                                <db2ToSql>                                                </db2ToSql>                                        </dateMask>                                </dateMasks>                        </conversionFormats>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|sourceFormat|drdaas:DateFormats||true|n/a|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The dateMask element contains a db2ToSql or sqlToDb2 to indicate the direction, and a sourceFormat and a targetFormat to specify the mapping.|