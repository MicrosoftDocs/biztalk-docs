---
description: "Learn more about: db2ToSql"
title: "db2ToSql1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb4c004f-8677-4b84-a7a7-959f9b302cd0
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# About db2ToSql
The db2ToSql defines the direction from DB2 to SQL Server.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<conversionFormats>  
\<timeMasks>  
\<timeMask>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <conversionFormats>                                <timeMasks>                                        <timeMask>                                                <db2ToSql>                                                </db2ToSql>                                        </timeMask>                                </timeMasks>                        </conversionFormats>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|sourceFormat|drdaas:TimeFormats||true|n/a|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The timeMask element contains a db2ToSql or sqlToDb2 to indicate the direction, and a sourceFormat and a targetFormat to specify the mapping.|
