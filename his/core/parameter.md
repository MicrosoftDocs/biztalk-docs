---
description: "Learn more about: parameter"
title: "parameter"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# parameter
Specifies the parameters for the  element.  
  
 \<hostIntegration.drdaAr.staticSql>  
\<packages>  
\<package>  
\<sections>  
\<section>  
\<statement>  
\<parameters>  
  
## Syntax  
  
```  
<hostIntegration.drdaAr.staticSql>       <packages>                <package>                        <sections>                                <section>                                        <statement>                                                <parameters>                                                        <parameter>                                                        </parameter>                                                </parameters>                                        </statement>                                </section>                        </sections>                </package>        </packages></hostIntegration.drdaAr.staticSql>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|name|xs:string|A name. DB2 for z/OS accepts a 128-byte string. DB2 for i5/OS accepts a 128-byte string. DB2 for Linux, UNIX, or Windows accepts a 128-byte string.|true|n/a|  
|type|drdaar:parameterTypes|Type is defined by using the name or abbreviation supported by the target DB2 server platform and version. See SQL Reference for supported values Valid values are|true|n/a|  
|length|xs:int|Length is defined by using the value supported by the target DB2 server platform and version. See SQL Reference for supported values.|true|n/a|  
|precision|xs:int|Precision is defined by using the value supported by the target DB2 server platform and version. See SQL Reference for supported values.|true|n/a|  
|scale|xs:int|Scale is defined by using the value supported by the target DB2 server platform and version. See SQL Reference for supported values.|true|n/a|  
|ccsid|xs:int|Coded Character Set Identifier is defined by using a value supported by the target DB2 server platform and version. See SQL Reference for supported values.|true|n/a|  
|nullable|xs:boolean|Nullability is specified by using true or false.|false|false|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The Parameters element contains one or more Parameter elements, which define the input and/or output parameters on the SQL statement.|
