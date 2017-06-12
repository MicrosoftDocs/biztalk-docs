---
title: "Document Version (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Document Version property [schemas]"
ms.assetid: ead7746a-5e7d-4cfd-b755-54327928d710
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Document Version (Node Property of All Schemas)
Use the **Document Version** property to specify the version of the schema that you are configuring, using whatever versioning scheme makes sense for your business.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Reference  
  
## Allowed Values  
 Any string allowed in XML.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 As the value of the **version** attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor.  
  
 This value will be used as the version number of instance messages.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)   
 [Document Type (Node Property of All Schemas)](../core/document-type-node-property-of-all-schemas.md)