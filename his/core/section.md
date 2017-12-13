---
title: "section | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f1cc24e-9123-451c-8706-5dd1a5955a31
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# section
The Section element described in the following table contains two attributes, Number and Alias. It also contains the following set of elements: Statement, Parameters and ResultSet.  
  
 \<hostIntegration.drdaAr.staticSql>  
\<packages>  
\<package>  
\<sections>  
  
## Syntax  
  
```  
<hostIntegration.drdaAr.staticSql>        <packages>                <package>                        <sections>                                <section>                                </section>                        </sections>                </package>        </packages></hostIntegration.drdaAr.staticSql>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|number|xs:int|Relational Database Package Section Number is an integer.|true|n/a|  
|alias|xs:string|Alias allows you to define a friendly package name for use with the Microsoft ADO.NET Data Provider for DB2.|false|n/a|  
  
### Child Elements  
  
|Element|Description|Occurance Constraint|  
|-------------|-----------------|--------------------------|  
||he Statement element described in the following table has one required attribute, Number, and a required value for the SQL statement command string.|0 to 1|  
||The Statement element described in the following table has one required attribute, Number, and a required value for the SQL statement command string.|1 to 1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||Sections is a collection of package Section elements.|