---
title: "parameters | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8ea1161-c7db-4afa-a8b5-02da009b0171
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
ms.author: "dwrede"
---
# parameters
The Parameters element contains one or more Parameter elements, which define the input and/or output parameters on the SQL statement.  
  
 \<hostIntegration.drdaAr.staticSql>  
\<packages>  
\<package>  
\<sections>  
\<section>  
\<statement>  
  
## Syntax  
  
```  
<hostIntegration.drdaAr.staticSql>        <packages>                <package>                        <sections>                                <section>                                        <statement>                                                <parameters>                                                </parameters>                                        </statement>                                </section>                        </sections>                </package>        </packages></hostIntegration.drdaAr.staticSql>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||TBD|1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The Statement element described in the following table has one required attribute, Number, and a required value for the SQL statement command string.|