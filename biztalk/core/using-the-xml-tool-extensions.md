---
title: "Using the XML Tool Extensions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5613bf15-6c0a-4a82-b200-24d0801d7ece
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the XML Tool Extensions
The XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enable you to perform tasks on schemas, maps, and message instances. You use these extensions at design time in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment. The tasks you can perform are:  
  
- **Validating a schema**. This operation validates an EDI schema based on EDI rules. For more information, see [Validating a Schema (EDI)](../core/validating-a-schema-edi.md).  
  
- **Validating a message instance**. This operation validates a single transaction set (without interchange and group headers) or a complete batched interchange with multiple transaction sets (with interchange and group headers). To validate an unbatched interchange, you need to remove the interchange and group headers from the instance. For more information, see [Validating an Instance (EDI)](../core/validating-an-instance-edi.md).  
  
- **Generating a message instance**. This operation generates either a complete batched interchange or a transaction set without interchange and group headers. You must specify the separators, identifiers, and other formatting used to generate the instance. For more information, see [Generating an Instance (EDI)](../core/generating-an-instance-edi.md).  
  
- **Testing a map**. This operation generates an output document (with fictitious data) based upon a source document and a map. For more information, see [Testing a Map](../core/testing-a-map.md).  
  
- **Validating a map**. This operation generates a file containing the underlying XSLT of the map and a file containing extension objects. For more information, see [Validating a Map (EDI)](../core/validating-a-map-edi.md).  
  
  In BizTalk Server, these extensions work on EDI schemas, maps, and message instances. These extensions enable you to work more effectively with complex EDI schemas, maps, and interchanges.  
  
  XML Tool extensions are enabled by default by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup program. If you double-click a schema in Solution Explorer of Visual Studio, the **Schema Editor Extensions** property of the schema is set to **EDI Schema Editor Extension**. This is required for the XML Tool extensions to function. You can select other schema editor extension while leaving the EDI extensions selected.  
  
## See Also  
 [Generating an Instance (EDI)](../core/generating-an-instance-edi.md)   
 [Validating an Instance (EDI)](../core/validating-an-instance-edi.md)   
 [Validating a Schema (EDI)](../core/validating-a-schema-edi.md)   
 [Testing a Map](../core/testing-a-map.md)   
 [Validating a Map (EDI)](../core/validating-a-map-edi.md)