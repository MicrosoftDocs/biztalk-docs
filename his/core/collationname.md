---
title: "collationName | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b5d3f07-9ee7-472b-b160-30e5d4cdea1a
caps.latest.revision: 2
ms.author: "dwrede"
---
# collationName
The collationName element must contain a from attribute and a to attribute to define a collation name mapping.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<collationNames>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <collationNames>                                <collationName>                                </collationName>                        </collationNames>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|from|xs:string|The from attribute instructs the DRDA Service SQL Transformer to convert from the specified collation-name string within a DB2 SELECT ORDER BY COLLATION_KEY clause. This required attribute accepts a string value. There is no default value.|true|n/a|  
|to|xs:string|The to attribute instructs the DRDA Service SQL Transformer to convert to the specified collation_name string within a SQL Server SELECT ORDER BY COLLATE clause. This required attribute accepts a string value. There is no default value.|true|n/a|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The collationNames element can contain one or more collationName elements to instruct the DRDA Service to convert from a DB2 collation-name value to a SQL Server collation_name value, when transforming a DB2 SELECT statement with ORDER BY COLLATION_KEY (collation-name) clause into a SQL Server SELECT statement with ORDER BY COLLATE (collation_name) clause.|