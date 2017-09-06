---
title: "Node Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 366080f0-c21a-467d-8051-fd280264c5c3
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Node Properties

## Overview
In BizTalk Editor, you examine and set node properties in the Visual Studio Properties window. As you select different types of nodes in the schema tree view, different sets of properties are displayed in the Properties window. As is standard in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], these properties can be displayed either in categories or alphabetically with no indication of their categories. Use the standard buttons near the top of the Properties window to toggle this setting.  
  
 Node properties, especially when set to values other than their defaults, are generally represented in the XML Schema definition (XSD) language as attributes and attribute values associated with the corresponding element. For example, when properties are set for the **Min Occurs** and **Max Occurs** properties, which are available for several different node types, the values that are set are used as the values of the **minOccurs** and **maxOccurs** attributes, respectively, associated with the element that represents the node for which the **Min Occurs** and **Max Occurs** properties are being set.  

## Property types
 The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] developer reference contains a reference section for the properties of the various node types, organized by category and alphabetically. The following summarize the properties associated with each node type:  
  
-   Schema Node Properties
  
-   Record Node Properties
  
-   Field Element Node Properties
  
-   Field Attribute Node Properties
  
-   Sequence Group Node Properties
  
-   Choice Group Node Properties 
  
-   All Group Node Properties
  
-   Attribute Group Node Properties
  
-   Any Element Node Properties
  
-   Any Attribute Node Properties
  
-   Equivalent Node Properties
  
-   Equivalent Child Node Properties

More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 **Node Properties — Alphabetical Listings** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] contains all of the individual reference topics for each node property, some of which apply to various types of nodes. The individual reference topics are categorized according to whether they are basic properties that apply to all types of schemas, or a specialized properties that are associated with a schema editor extension, such as the flat file extension. Within these categories, they are listed alphabetically.  
  
 BizTalk Editor uses the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window to enable you to examine and set the properties of the nodes in the schema tree. This section describes some characteristics of working with properties in the Properties window, including special considerations for the **Node Name** property, an explanation of the interdependencies between properties, and information about the maximum lengths allowed for certain properties or types of properties.  
  
 The remainder of this section provides additional information about particular, special node properties and other information that applies generally to node properties.  
  
## Next steps
  
-   [Node Name Property](../core/node-name-property.md)  
  
-   [Property Interdependencies](../core/property-interdependencies.md)  
  
-   [Additional Flat File Properties](../core/additional-flat-file-properties.md)