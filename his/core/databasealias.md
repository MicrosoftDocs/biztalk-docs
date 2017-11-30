---
title: "databaseAlias | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a7b3d6a-8af1-4f0d-8eda-dad0ad7461c7
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# databaseAlias
The databaseAlias element contains a sourceLocation, sourceCollection, targetDatabase, and targetSchema to define one or more optional object name mappings.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<databaseAliases>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <databaseAliases>                                <databaseAlias>                                </databaseAlias>                        </databaseAliases>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|sourceLocation|xs:string|The sourceLocation attribute defines an in-bound DRDA RDBNAM (Relational Database Name) that the DRDA Service should use when mapping to an out-bound SQL Server database name. This optional property accepts a string value. The default value is an empty string, which denotes any value.|true|n/a|  
|sourceCollection|xs:string|The sourceCollection attribute defines an in-bound DRDA COLID (Collection Identifier) that the DRDA Service should use when mapping to an out-bound SQL Server schema name. This optional attribute accepts a string value. The default value is an empty string, which denotes any value.|true|n/a|  
|targetDatabase|xs:string|The targetDatabase attribute defines an out-bound SQL Server database name that the DRDA Service should use when mapping from an in-bound DRDA RDBNAM value. This optional attribute accepts a string value. The default value is an empty string, which denotes any value.|true|n/a|  
|targetSchema|xs:string|The targetSchema attribute defines an out-bound SQL Server schema name that the DRDA Service should use when mapping from an in-bound DRDA COLID value. This optional attribute accepts a string value. The default value is an empty string, which denotes any value.|true|n/a|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The databaseAliases element instructs the DRDA Service to map in-bound catalog and schema names to outbound catalog and schema names, for use when executing static SQL packages for DB2 commands mapped to SQL Server stored procedures.|