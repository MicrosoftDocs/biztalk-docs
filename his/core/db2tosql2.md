---
title: "db2ToSql2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b16e89e-a3da-4809-8dc4-7b0d0beb6fc4
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# db2ToSql
The db2ToSql defines the direction from DB2 to SQL Server.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<conversionFormats>  
\<dateTimeMasks>  
\<dateTimeMask>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <conversionFormats>                                <dateTimeMasks>                                        <dateTimeMask>                                                <db2ToSql>                                                </db2ToSql>                                        </dateTimeMask>                                </dateTimeMasks>                        </conversionFormats>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|sourceFormat|drdaas:TimeStampFormats||true|n/a|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The dateTimeMask element contains a db2ToSql or sqlToDb2 to indicate the direction, and a sourceFormat and a targetFormat to specify the mapping.|