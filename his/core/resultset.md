---
title: "resultSet | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7294d155-30c0-4c8d-a768-665c241786e0
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# resultSet
The Statement element described in the following table has one required attribute, Number, and a required value for the SQL statement command string.  
  
 \<hostIntegration.drdaAr.staticSql>  
\<packages>  
\<package>  
\<sections>  
\<section>  
  
## Syntax  
  
```  
<hostIntegration.drdaAr.staticSql>        <packages>                <package>                        <sections>                                <section>                                        <resultSet>                                        </resultSet>                                </section>                        </sections>                </package>        </packages></hostIntegration.drdaAr.staticSql>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurance Constraint|  
|-------------|-----------------|--------------------------|  
||TBD.|1 to 1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The Section element described in the following table contains two attributes, Number and Alias. It also contains the following set of elements: Statement, Parameters and ResultSet.|