---
description: "Learn more about: sections"
title: "sections | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d77b1b58-8869-4379-9284-ed28b96dd75e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# sections
Sections is a collection of package elements.  
  
 \<hostIntegration.drdaAr.staticSql>  
\<packages>  
\<package>  
  
## Syntax  
  
```  
<hostIntegration.drdaAr.staticSql>        <packages>                <package>                        <sections>                        </sections>                </package>        </packages></hostIntegration.drdaAr.staticSql>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The Section element described in the following table contains two attributes, Number and Alias. It also contains the following set of elements: Statement, Parameters, and ResultSet.|1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The Package element contains the following set of attributes: Collection, Id, Token, Isolation Level, Version, and Sections Collection.|
