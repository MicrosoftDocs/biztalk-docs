---
description: "Learn more about: collationNames"
title: "collationNames"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
