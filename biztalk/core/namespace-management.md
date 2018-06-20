---
title: "Namespace Management | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4638c47c-3cdd-43af-aa00-da98e7293503
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Namespace Management
BizTalk Editor provides support for namespaces. An XML namespace is a collection of names that can be used as element or attribute names in an XML message. The namespace qualifies element and attribute names to avoid conflicts between the same element and attribute names that might be defined elsewhere within the same schema.  
  
 Namespaces are identified by a Universal Resource Identifier (URI), either as a Uniform Resource Locator (URL) or a Uniform Resource Name (URN). They are also given a typically short prefix alias that is prepended with a separating colon (:) from the element or attribute name itself. For example, it is common to see the following namespace declaration within the **schema** element in the XSD representation of the schema.  
  
```  
xmlns:xs="http://www.w3.org/2001/XMLSchema"  
  
```  
  
 The prefix is xs, which you see throughout the XSD representation, qualifying such elements as the **element** element (xs:element) and the **attribute** element (xs:attribute).  
  
 When you first create a new schema, regardless of whether it is a message schema or a property schema, it is important to set the **Target Namespace** property of the **Schema** node properly. You need to establish the target namespace before the schema is used by another schema with the import/include/redefine mechanisms, and before any property promotions are defined.  
  
> [!WARNING]
>  If you will be using two namespaces that vary only by case, the BizTalk database must be installed with a case-sensitive collation. Examples of case-sensitive collations include binary and non-binary collations with case-sensitivity enabled. If this is not done, schema resolution will fail because XML is case-sensitive.  
  
 The following two namespaces are automatically added as namespace declarations to the schema element in the XML Schema definition (XSD) language representation of the schema:  
  
- xmlns:b="<http://schemas.microsoft.com/BizTalk/2003>"  
  
- xmlns:xs="<http://www.w3.org/2001/XMLSchema>"  
  
  In the course of using other schemas within the schema you are creating, other namespaces will be declared. You can examine these namespaces, as well as the automatically included namespaces, in the **Imports** dialog box that you can access by using the **Imports** property of the **Schema** node. For more information about using other data types declared in other schemas within the schema you are creating, see [Schemas That Use Other Schemas](../core/schemas-that-use-other-schemas.md) and [Creating Schemas That Use Other Schemas](../core/how-to-create-schemas-that-use-other-schemas.md).  
  
  Namespaces associated with property schemas can be examined in the **Promote Properties** dialog box.  
  
## See Also  
 [Considerations When Creating Schemas](../core/considerations-when-creating-schemas.md)