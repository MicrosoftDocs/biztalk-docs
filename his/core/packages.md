---
title: "packages | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 273defee-481b-4586-b217-a73dfc858573
caps.latest.revision: 5
author: MandiOhlinger
manager: anneta
ms.author: "dwrede"
---
# packages
The Packages root element contains a set of nested elements consisting of Options and Package. There may be one Options element per document. There must be at least one Package element per document, as described in the following table  
  
 \<hostIntegration.staticSql>  
  
## Syntax  
  
```  
<hostIntegration.staticSql>        <packages>        </packages></hostIntegration.staticSql>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The Package element contains the following set of attributes: Collection, Id, Token, Isolation Level, Version and Sections Collection.|1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||TBD|