---
description: "Learn more about: statement"
title: "statement"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# statement
The Statement element described in the following table has one required attribute, Number, and a required value for the SQL statement command string.  
  
 \<hostIntegration.drdaAr.staticSql>  
\<packages>  
\<package>  
\<sections>  
\<section>  
  
## Syntax  
  
```  
<hostIntegration.drdaAr.staticSql>        <packages>                <package>                        <sections>                                <section>                                        <statement>                                        </statement>                                </section>                        </sections>                </package>        </packages></hostIntegration.drdaAr.staticSql>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|number|xs:int|Statement Number|false|n/a|  
|sqlStatement|xs:string|SQL Statement|true|n/a|  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The Parameters element contains one or more Parameter elements, which define the input and/or output parameters on the SQL statement.|1 to 1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The Section element described in the following table contains two attributes, Number and Alias. It also contains the following set of elements: Statement, Parameters, and ResultSet.|
