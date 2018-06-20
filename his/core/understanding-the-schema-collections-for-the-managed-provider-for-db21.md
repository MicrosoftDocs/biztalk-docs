---
title: "Understanding the Schema Collections for the Managed Provider for DB21 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe6927a4-dc84-4a1b-897f-7ef7499b7575
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Understanding the Schema Collections for the Managed Provider for DB2
The following tables describe the schema collections that are implemented by the Managed Providers for DB2. You can query the Managed Provider for DB2 to determine the list of supported schema collections by calling the `GetSchema` method with no arguments, or with the schema collection name "MetaDataCollections". This returns a `DataTable` object with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use. These collections describe all of the required columns. If a provider cannot determine the value of a required column, it returns `null`.  
  
 **Common Schema Collections**  
  
- MetaDataCollections  
  
- DataSourceInformation  
  
- DataTypes  
  
- Restrictions  
  
- ReservedWords  
  
  **Provider-Specific Collections**  
  
- Tables  
  
- Columns  
  
- Procedures  
  
- ProcedureParameters  
  
- Incexes  
  
- PrimaryKeys  
  
- ForeignKeys  
  
- TablePrivileges  
  
- Statistics  
  
## Example  
  
## See Also  
 [Obtaining Schema Information from the Managed Provider for DB2](../core/obtaining-schema-information-from-the-managed-provider-for-db22.md)