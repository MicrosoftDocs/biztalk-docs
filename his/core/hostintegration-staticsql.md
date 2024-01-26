---
description: "Learn more about: hostIntegration.staticSql"
title: "hostIntegration.staticSql"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# hostIntegration.staticSql
The Microsoft static SQL for DB2 custom package XML file contains multiple elements to inform the DRDA Client and DRDA Server how to execute the DRDA commands BGNBND (Begin Binding a Package to an RDB) with BNDOPT (Bind Options) and BNDSQLSTT (Bind SQL Statement to an RDB Package). The HostIntegrationStaticSql.xsd describes the XML elements, attributes and values that you can define to describe the static SQL package bind options, package name, package sections, statements, parameters, and result sets.  
  
## Syntax  
  
```  
<hostIntegration. staticSql></hostIntegration.staticSql>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The Options element contains a set of optional attributes used for binding custom static SQL packages|1|  
||The Packages root element contains a set of nested elements consisting of Options and Package. There may be one Options element per document. There must be at least one Package element per document, as described in the following table|1 to 1|  
  
### Parent Elements  
 None
