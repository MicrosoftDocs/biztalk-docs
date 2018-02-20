---
title: "package | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 526fa138-3e9b-4709-ae15-08abb19ea38c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# package
The Package element contains the following set of attributes: Collection, Id, Token, Isolation Level, Version, and Sections Collection.  
  
 \<hostIntegration.drdaAr.staticSql>  
\<packages>  
  
## Syntax  
  
```  
<hostIntegration.drdaAr.staticSql>        <packages>                <package>                </package>        </packages></hostIntegration.drdaAr.staticSql>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|token|xs:string|Consistency Token is an 8-byte string.|false|n/a|  
|version|xs:string|Version Name is a 254-byte string.|false|n/a|  
|collection|xs:string|DB2 for z/OS accepts a 128-byte string. DB2 for i5/OS accepts a 10-byte string. DB2 for LUW accepts a 30-byte string.|true|n/a|  
|id|xs:string|Unique identifier (name) is a 128-byte string.|true|n/a|  
|isolationLevel|drdaar:OptionsIsolationLevel|Isolation Level. Valid values are|false|CursorStability|  
|title|xs:string|Title is a 255-byte string.|false|n/a|  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||Sections is a collection of package Section elements.|1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The Packages root element contains a set of nested elements consisting of Options and Package. There may be one Options element per document. There must be at least one Package element per document, as described in the following table:|