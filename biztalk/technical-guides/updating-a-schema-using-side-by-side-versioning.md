---
title: "Updating a Schema Using Side-by-Side Versioning | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7360ec5-b5e9-40c7-9a7c-965fcc95ddb0
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Updating a Schema Using Side-by-Side Versioning
You can perform side-by-side versioning with schemas. You do so by adding a new version of the schema to an assembly, upgrading the version of the schema, while leaving the existing schema (and its version) unchanged.  
  
 If you increment a schema version, you must update the reference to the schema for any pipeline instances and pipeline components that use it. You must also update the maps that reference the schema (or create new maps) as well as any orchestrations that rely on the schema.  
  
 If you undeploy a schema, the previous version of the schema, if available, will become active.  
  
## Schema Resolution in Pipelines  
 If you add to an application an assembly that includes a new schema with the same message type as an existing schema in the BizTalk group, the schema with the latest version number will be used when schema resolution occurs in pipelines. If one message type refers to more than one .NET type, this ambiguity may cause pipeline execution failure. This is because schema lookup uses message type, the target namespace, and root name of the instance. This type of failure can occur for pipelines in any application that uses a schema with the same message type as the new schema. For more information about schema resolution, see [Schema Resolution in Pipeline Components](http://go.microsoft.com/fwlink/?LinkID=154207) (<http://go.microsoft.com/fwlink/?LinkID=154207>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
 The schema resolution behavior for the XML Disassembler may require additional changes after adding a new version of a schema side by side with an older version. In certain cases, you may want to hard-code references in the pipeline disassembler properties in the Pipeline Designer to specific versions of the schemas. This enables you to avoid the dynamic resolution behavior, in which the XML Disassembler determines which schema to load by using the message type dynamically discovered at runtime from the message XML content.  
  
## Updating a Schema in an Orchestration  
 When you change the schema associated with multiple send and receive shapes in an orchestration, you can make changes much easier by setting the Message Type property for the message associated with each send or receive shape to Multi-part Message Type, rather than Schema. You can then set the Type property for the message part associated with each shapes to be the same schema. By so doing, you can subsequently change the schema by changing the Type property for each message part, rather than having to change the Message Type for each shape. For more information about making changes easier by this process, see the [8 Tips and Tricks for Better BizTalk Programming](http://go.microsoft.com/fwlink/?LinkId=101594) white paper (http://go.microsoft.com/fwlink/?LinkId=101594).  
  
## Versioning Schemas  
 BizTalk Server takes a schema from the most recent version of the assembly containing it. This means that if you create a new version of a schema, the new version completely replaces all previous versions of the schema. This works well when transactions are short-lived. However, transactions in the Business Process Management solution are long-lived: an order may take up to a year to complete.  
  
 To allow for the possibility of using multiple versions of a schema being in use, each schema in the solution includes a version number in its namespace. BizTalk pipelines determine the message type of a message based on the target namespace plus the root node name defined in the schema. For example, the namespace for the Order schema is as follows:  
  
```  
http://Microsoft.Samples.BizTalk.SouthridgeVideo.Schemas.Order.v1  
```  
  
 Because the namespace identifies the schema, and inclusion of the version number makes the namespace unique to the schema, the new schema will be distinct from the older version. Thus, a new schema can be used without supplanting the old schema.  
  
 Changing the schema version can affect many parts of your solution, so this should be planned in advance. For more information about the effect of schema version changes, see [Schema Resolution in Pipeline Components](http://go.microsoft.com/fwlink/?LinkID=154207) (<http://go.microsoft.com/fwlink/?LinkID=154207>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
 When changing the version of schemas in an orchestration, use multipart message types. Doing so will result in greater flexibility when versioning schemas. For more information about the advantages of using multipart message types, see tip #1, “Always Use Multi-Part Message Types,” in the MSDN Magazine article [8 Tips And Tricks For Better BizTalk Programming](http://go.microsoft.com/fwlink/?LinkId=101594) (http://go.microsoft.com/fwlink/?LinkId=101594).  
  
## See Also  
 [Best Practices for Updating Applications](../technical-guides/best-practices-for-updating-applications.md)