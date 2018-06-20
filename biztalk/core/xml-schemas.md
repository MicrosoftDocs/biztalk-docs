---
title: "XML Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ec364e7-866d-4164-be91-be75a40ce878
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XML Schemas
An XML schema describes a business document that is represented in XML. Because Microsoft BizTalk Server uses XML as its canonical representation for business documents, inbound and outbound documents do not require any translation. XML schemas can be created in BizTalk Editor using only the basic set of properties that are available within all schemas, and do not require any schema editor extensions to be enabled.  
  
 There are several ways in which you can create XML schemas in BizTalk Server. These include:  
  
- **Creating a new schema**. This method of schema creation involves adding a new schema to a BizTalk project. In **Solution Explorer**, right-click the BizTalk project, click **Add**, click **New Item**, and then click **Schema**. Build up the structure of the schema by adding various nodes in the schema tree view.  
  
- **Creating a new schema, in conjunction with other schemas**. For complex schemas in the real world, you are more likely to build the schemas for your messages by using types provided in other existing schemas. By using the XML Schema definition (XSD) language concepts of importing, including, and redefining schemas, you can take advantage of types already defined in other schemas. For more information about using multiple schemas together, see [Schemas That Use Other Schemas](../core/schemas-that-use-other-schemas.md).  
  
- **Generating a schema from an instance message**. You can generate an XML schema that corresponds to a particular instance message as long as that instance message consists of well-formed XML. Use the **Add Generated Items - *\<BizTalk Project Name\>*** dialog box, accessed by clicking **Add Generated Items** on the **Project** menu, to perform this type of schema generation operation.  
  
  > [!NOTE]
  >  This type of generation operation can only be used to generate XML schemas, not property schemas or flat file schemas.  
  
- **Migrating a schema from an older schema specification language to XSD**. You can generate an XML schema for BizTalk Server from a schema that was developed by using a previous version of BizTalk Server, which stored schemas in XML-Data Reduced (XDR) format. For more information about how to migrate older XDR schemas to the XSD format used by BizTalk Server, see [Schema Migration from Previous Versions of BizTalk Server](../core/schema-migration-from-previous-versions-of-biztalk-server.md).  
  
   You can also generate an XML schema based on XSD from a document schema expressed by using the Document Type Definition (DTD) syntax.  
  
   Use the **Add Generated Items - *\<BizTalk Project Name\>*** dialog box, accessed by clicking **Add Generated Items** on the **Project** menu, to perform this type of schema generation operation.  
  
  > [!NOTE]
  >  These types of generation operations can only be used to generate XML schemas, not property schemas or flat file schemas.  
  
  Whichever schema creation technique you use, you will continue by modifying the schema so that it provides a sufficiently complete description of its corresponding instance messages. To get started on these tasks, see [Managing the Nodes Within a Schema](../core/managing-the-nodes-within-a-schema.md), [Setting Node Properties](../core/how-to-set-node-properties.md), and [Working with Existing Nodes](../core/working-with-existing-nodes.md).  
  
## See Also  
 [Different Types of BizTalk Schemas](../core/different-types-of-biztalk-schemas.md)