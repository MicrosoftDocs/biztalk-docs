---
description: "Learn more about: service"
title: "service"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# service
The service element defines the configuration for the DrdaService1 service.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|name|xs:string|The service name DrdaService1 defines the single runtime instance of the DRDA Server.|true|n/a|  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The applicationEncodings element contains applicationEncoding elements for specifying default application-level encoding schemes on a per-database basis.|0 to 1|  
||The collationNames element can contain one or more collationName elements to instruct the DRDA Service to convert from a DB2 collation-name value to a SQL Server collation_name value, when transforming a DB2 SELECT statement with ORDER BY COLLATION_KEY (collation-name) clause into a SQL Server SELECT statement with ORDER BY COLLATE (collation_name) clause.|0 to 1|  
||The connectionManager element contains the network, security and failover settings for managing in-bound DRDA client connections.|1 to 1|  
||The conversionBehavior element is for use by Transaction Integrator only. The DRDA Service does not require this element.|0 to 1|  
||The conversionFormats element contains dateMasks, timeMasks, and dateTimeMasks for converting to and from DB2 and SQL Server datetime formats.|0 to 1|  
||The database element contains the network settings for managing out-bound SQL client connections.|1 to 1|  
||The databaseAliases element instructs the DRDA Service to map in-bound catalog and schema names to outbound catalog and schema names, for use when executing static SQL packages for DB2 commands mapped to SQL Server stored procedures.|0 to 1|  
||The drdaServiceTraceListeners element contains one or more drdaServiceTraceListener elements to instruct the DRDA Server to send trace output to optional custom text trace listeners.|0 to 1|  
||The packageBindListeners element contains one or more packageBindListener elements to instruct the DRDA Server to send bind package with bind SQL statement output to optional custom bind listeners.|0 to 1|  
||The securityManager element contains the security settings|1 to 1|  
||The sqlApplicationManager element contains the application settings for managing out-bound SQL client connections.|1 to 1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The services element contains the specifications for all services the application hosts.|
