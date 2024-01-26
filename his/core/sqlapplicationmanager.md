---
description: "Learn more about: sqlApplicationManager"
title: "sqlApplicationManager"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# sqlApplicationManager
The sqlApplicationManager element contains the application settings for managing out-bound SQL client connections.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <sqlApplicationManager>                        </sqlApplicationManager>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|type|xs:string|The sqlApplicationManager type is the Microsoft.HostIntegration.Drda.Server.SqlApplicationManager, which processes the out-bound SQL client connections.|true|n/a|  
|connectionCacheTimeout|xs:duration|The DRDA Service will pool out-bound SQL Client connections to remote SQL Server computers. The connectionCacheTimeout attribute instructs the DRDA Server to retain a pooled connection for a duration of time, after which to obtain a new SQL client connection. This optional attribute accepts a duration value. The default value is PT8H (period of time is 8 hours). The duration value is specified in the form PnYnMnDTnHnMnS.|false|P1D|  
|connectionCacheSize|xs:int|The DRDA Service will pool out-bound SQL Client connections to remote SQL Server computers. The connectionCacheSize attribute defines the number of SQL Client to SQL Server computer connections the DRDA Service will cache in the SQL Client Connection Pool. This optional attribute accepts an integer value. The default value is 1000.|false|1000|  
|rollbackTransactionOnError|xs:boolean|The rollbackTransactionOnError attribute instructs the DRDA Service to execute a ROLLBACK following a negative SQL Server database error. This optional attribute accepts a Boolean value. The default value is true.|false|true|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The service element defines the configuration for the DrdaService1 service.|
