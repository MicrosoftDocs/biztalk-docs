---
description: "Learn more about: Source and Destination Schemas"
title: "Source and Destination Schemas"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Source and Destination Schemas
Each BizTalk map uses two schemas: a source schema and a destination schema. A source schema defines the structure of the instance messages from which you are taking data. The destination schema defines the structure of the instance messages the map produces. For example, if you want to map the shipping and billing information from a purchase order to an invoice, you need a schema to define purchase orders for the source schema and a schema defining invoices for the destination schema.  
  
 Schemas used in BizTalk maps must meet the following conditions:  
  
- The source and destination schemas need to be a part of your current BizTalk project, or you must include a reference to the schemas in the assembly so that the schemas can be accessed during run time.  
  
- The schemas used in BizTalk Mapper must be based on the XML Schema definition (XSD) language. BizTalk Editor provides an easy way to create such schemas. For more information about creating schemas with BizTalk Editor, see [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md). Also see [Creating Schemas](../core/creating-schemas.md).  
  
  In BizTalk Editor, you can create schemas with multiple root nodes. However, if you use a schema with multiple root nodes in a BizTalk map, you must choose which root node (and corresponding substructure) to use in the map. Schemas have a **Root Reference** property identifying which root is primary. If a schema has multiple roots and the **Root Reference** property is set when the schema is first opened as the source or destination schema, BizTalk Mapper uses the specified root. If a schema has multiple roots and the **Root Reference** property is not set, BizTalk Mapper prompts you to choose a root.  
  
  If you change the **Root Reference** property of a schema already used in a map, BizTalk Mapper does not notice the change and continues to use the originally specified root. If you want to build different maps using different roots of the same schema, it is best not to set the **Root Reference** property. That way, whenever the schema is used for a new map, you must explicitly choose the root.  
  
  If you edit a schema after it is included in a map, the links within the map may break.  
  
## See Also  
 [Maps](../core/maps.md)   
 [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md)
