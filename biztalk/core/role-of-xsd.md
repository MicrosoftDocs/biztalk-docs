---
description: "Learn more about: Role of XSD"
title: "Role of XSD"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Role of XSD
The XML Schema definition (XSD) language provides the underlying syntax of the message schemas defined within BizTalk. Although the tree views in BizTalk Editor and BizTalk Mapper use a BizTalk-specific graphical hierarchy of record and field nodes (among other types of nodes), each with its own set of properties, such hierarchies are constructed and persisted as XSD. BizTalk Editor provides a read-only XSD view in which you can see the XSD that is constructed as various nodes are added to or removed from the graphic representation of the schema in the tree view, and as the values of the properties associated with those nodes are changed. Although it is usually not necessary to understand the details of XSD to successfully construct simple schemas with BizTalk Editor, if you study the XSD changes as you make changes to the schema hierarchy in the tree view, you will learn to use XSD.  
  
 The schema annotation feature within XSD, with the extensive set of annotations defined by BizTalk Server, effectively allows XSD to be extended to support the necessary semantics for representing non-XML messages such as flat files.  
  
## See Also  
 [XSD Resources on the Web](../core/xsd-resources-on-the-web.md)   
 [About Schemas](../core/about-schemas.md)
