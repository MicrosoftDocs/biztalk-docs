---
title: "Types of Links | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "compiler directives, links"
  - "elastic links [maps]"
  - "maps, links"
  - "BizTalk Mapper, links"
  - "partial links [maps]"
  - "fixed links [maps]"
ms.assetid: 348fae77-2e25-4b79-93bb-d42f3d18a3f7
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Types of Links
The following list summarizes the various types of links available in BizTalk Mapper:  
  
- **Elastic links.** The term elastic applies to a link as it is being created, before both ends of the link are connected. For example, if you are dragging a link from a field in the source schema, but you have not yet connected it to its corresponding field in the destination schema, the link is elastic. As you complete the connection, the elastic link becomes a fixed link.  
  
   You can drag one endpoint of a link to another node or a functoid. For more information about link replacement, see [How to Create Links](../core/how-to-create-links.md).  
  
- **Fixed Links.** The term fixed applies to a link that you have explicitly constructed to represent the movement of a value from a source instance message to a destination instance message, or at least a part of that movement. Fixed links that directly connect a **Record** or **Field** node in the source schema to a **Record** or **Field** node in the destination schema represent a straight copying of data at run time. Fixed links connecting to a functoid at one end or the other represent part of the movement of data from an input instance message to an output instance message at run time. Several of these together, completing the link between the source and destination schemas, represent the entire movement of an item of data.  
  
- **Partial links.** The term partial applies to links for which you cannot currently see the exact **Record** or **Field** node to which they are connected in the source or destination schemas. This occurs when the **Record** or **Field** node to which they are attached is not shown because one of its ancestor nodes is collapsed in the tree representation of the schema. For more information about partial links, see [How to Optimize the Display of Links](../core/how-to-optimize-the-display-of-links.md).  
  
- **Compiler links.** The term compiler applies to links that BizTalk Mapper creates automatically when you build a BizTalk project. For example, if you configure table-driven looping, the compiler links show the relationship and the links between the records and fields in the source schema and the records and fields in the destination schema. This type of link can be generated automatically by compiler directives, or it can be user-directed.  
  
  BizTalk Mapper, by default, displays these various types of links using different colored lines to help you distinguish the detail of your maps. You can change the colors used for these different kinds of links with the **Options** command on the **Tools** menu. For more information about how change in color renders different categories of links, see [How to Customize Colors and Font in BizTalk Mapper](../core/how-to-customize-colors-and-font-in-biztalk-mapper.md).  
  
## See Also  
 [Using Links to Specify Record and Field Mappings](../core/using-links-to-specify-record-and-field-mappings.md)