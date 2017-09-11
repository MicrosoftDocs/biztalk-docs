---
title: "Links in Maps | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "functoid types, Looping"
  - "Looping functoids"
  - "maps, links"
  - "BizTalk Mapper, links"
ms.assetid: 3db77b8d-7b86-4c00-99a0-0513aff9b56b
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Links in Maps
Links specify the basic function of copying data from an element or attribute in an input instance message to an element or attribute in an output instance. You create links between records and fields in the source and destination schemas at design time. This drives the creation, at run time, of an output instance message conforming to the destination schema from an input instance message conforming to the source schema.  
  
 BizTalk Mapper supports one-to-one links and one-to-many links. For example, a link can connect a single record or field from the source schema to a single record or field in the destination schema. A link can also connect a single record or field from the source schema to multiple records or fields in the destination schema.  
  
 Links can also connect multiple records or fields from the source schema to a functoid, which then connects to a single (or multiple) record(s) and/or field(s) in the destination schema. In general, direct links from multiple source records or fields to a single destination record or field are not valid and produce a warning. One exception to this is the **Looping** functoid. For more information about the **Looping** functoid, see [Looping Functoid](../core/looping-functoid.md).  
  
 The topics in this section describe concepts related to creating and working with links in BizTalk Mapper.  
  
## In This Section  
  
-   [Types of Links](../core/types-of-links.md)  
  
-   [Creating Links](../core/creating-links.md)  
  
-   [Configuring Links](../core/configuring-links.md)  
  
-   [Record-to-Record Linking](../core/record-to-record-linking.md)  
  
-   [Links To and From the Any Element and anyAttribute Nodes](../core/links-to-and-from-the-any-element-and-anyattribute-nodes.md)  
  
-   [Compiler Directives and Links](../core/compiler-directives-and-links.md)