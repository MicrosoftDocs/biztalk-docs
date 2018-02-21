---
title: "Add Project Items | Microsoft Docs"
description: Add orchestrations, schemas, maps, and pipelines to your BizTalk Server project in Visual Studio
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1b922d5-8ece-4e1a-a390-e6ae1222665a
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Add Project Items
In the context of the BizTalk project system, a project item is a configured item, such as a map or schema. A BizTalk application might contain one or more orchestrations, schemas, maps, and pipelines.  
  
> [!NOTE]
>  When you add an item to a project, do not use a period (.) in the name because a period is a separator for the .NET namespace. If you use a period in the item name, the Type Name of the item will contain an underscore (_) instead of a period.  
  
> [!NOTE]
>  When you add a schema, map, or pipeline to a folder, the **Fully Qualified Name** property is automatically generated and includes the namespace and type.  
  
## Orchestrations  
 An orchestration is a representation of a business process expressed in the XLANG/s language. XLANG/s can be used to complement existing procedural languages such as Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] and Microsoft [!INCLUDE[btsVBNet](../includes/btsvbnet-md.md)].  
  
 You can use Orchestration Designer to create the orchestrations that you want to include in a BizTalk project. All orchestrations that you create in Orchestration Designer have an .odx file extension.  
  
## Schemas  
 A schema is the definition of the structure for a document or message. It contains property information as it pertains to the records and fields within the structure. If appropriate, a schema can contain multiple subschemas.  
  
 You can use BizTalk Editor to import, edit, or create schemas. You can then use the schemas that you create to generate maps in BizTalk Mapper. All schemas that you save by using BizTalk Editor have an .xsd file extension.  
  
 For more information about schemas and BizTalk Editor, see [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md).  
  
## Maps  
 A map is an XML file that defines the correspondence between the records and fields in one schema and the records and fields in another schema. You create maps based on industry standards, non-industry standards (such as internal standards or legacy issues), or existing files. You create maps when you want to transform data that you receive or send from one format to another. You can use BizTalk Mapper to create maps that you include in a BizTalk project. All maps that you save in BizTalk Mapper have a .btm file extension. For more information about BizTalk Mapper, see [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md).  
  
## Pipelines  
 You can use Pipeline Designer to create receive and send pipelines. A pipeline is a software infrastructure that defines and links one or more stages for processing messages received or sent by BizTalk Server. The pipelines implement the stages in a specific order and include functions such as encoding or decoding, assembling or disassembling, and encrypting or decrypting.  
  
 The default pipeline references included in a BizTalk project can process only XML documents. If you want to process flat files, EDI documents, or other file types, you must create new pipelines as appropriate. All pipelines created with Pipeline Designer have a .btp extension. For more information about pipelines and Pipeline Designer, see [Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md).  
  
## Valid Files for BizTalk Projects  
 When you work with a BizTalk project, you can include many different files, such as HTML files, XML files, receive pipeline files, and schema files. With BizTalk Server, the assembly can contain any object supported by the Visual Studio build system.  
  
## See Also  
 [Working with BizTalk Projects](../core/working-with-biztalk-projects.md)