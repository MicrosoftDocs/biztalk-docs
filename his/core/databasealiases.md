---
description: "Learn more about: databaseAliases"
title: "databaseAliases"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# databaseAliases
The databaseAliases element instructs the DRDA Service to map in-bound catalog and schema names to outbound catalog and schema names, for use when executing static SQL packages for DB2 commands mapped to SQL Server stored procedures.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <databaseAliases>                        </databaseAliases>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The databaseAlias element contains a sourceLocation, sourceCollection, targetDatabase, and targetSchema to define one or more optional object name mappings.|1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The service element defines the configuration for the DrdaService1 service.|
