---
title: "Target Namespace (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Target Namespace property [schemas]"
ms.assetid: 6067d3a3-f8f4-4ba4-b6c3-175755b90d67
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Target Namespace (Node Property of All Schemas)
Use the **Target Namespace** property to configure the target namespace for the schema using any valid uniform resource identifier (URI).  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 General  
  
## Allowed Values  
 Any valid URI.  
  
## Default Value  
 http://*ProjectName*.*SchemaName*, where "*ProjectName*" is the name of the project in which the schema was created and "*SchemaName*" is the name of the schema (without the XSD file extension. If either the project name or the schema name contains spaces, they are replaced with underscore (_) characters. For example, if the project name is "BizTalk Server Project2" and the schema name is "Project 3", the default target namespace value will be:  
  
 http://BizTalk_Server_Project2.Schema_3  
  
## XSD Persistence  
 As the value of the **targetNamespace** attribute of the **schema** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Schema** node in BizTalk Editor.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 If you use "x-schema" in the **targetNamespace** attribute value, you may cause a test failure when you test the instance in BizTalk Mapper.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)