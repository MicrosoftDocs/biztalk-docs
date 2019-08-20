---
title: "collationNames | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 026b9aa2-85af-41a9-9dbf-9e7e810cb1e8
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# collationNames
The collationNames element can contain one or more collationName elements to instruct the DRDA Service to convert from a DB2 collation-name value to a SQL Server collation_name value, when transforming a DB2 SELECT statement with ORDER BY COLLATION_KEY (collation-name) clause into a SQL Server SELECT statement with ORDER BY COLLATE (collation_name) clause.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <collationNames>                        </collationNames>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The collationName element must contain a from attribute and a to attribute to define a collation name mapping.|1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The service element defines the configuration for the DrdaService1 service.|