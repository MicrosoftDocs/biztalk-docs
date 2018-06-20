---
title: "Browse, search, and get metadata for Oracle E-Business Suite operations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05a0656c-84d0-4f25-9571-90a9df587b8c
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Browse, search, and get metadata for Oracle E-Business Suite operations
This section provides information about how to use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] and the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]. By using these [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components, you can:  
  
- Browse for operations to retrieve metadata.  
  
- Search for operations to retrieve metadata.  
  
- Add message schemas for selected operations and port binding configuration files to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] project when using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
- Add a WCF client class or a WCF service contract (interface) for selected operations and a configuration file (app.config) to a non-BizTalk programming project when using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
## How is the Metadata Categorized?  
 The [!INCLUDE[consumeadapterservshort_md](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] gives three different views of the artifacts available in the Oracle E-Business Suite server you connect to—**Application-based view**, **Artifact-based view**, and the **Schema-based view**. Why do you need three different views for the same set of artifacts? The following table lists the reasons why you should you use a specific view.  
  
|View|When do you use it|  
|----------|------------------------|  
|**Application-based view**|This view is categorized by the Oracle E-Business Suite application names. Use this view when you know which application contains the artifacts you want to work with.|  
|**Artifact-based view**|This view is categorized by the Oracle E-Business Suite artifacts. Use this view when you know which Oracle E-Business Suite artifact you want to work with but you are not sure which application the artifact belongs to. Using this view, you can search for a specific artifact across all Oracle E-Business Suite applications.<br /><br /> The artifact-based view also lists the artifacts in the underlying Oracle database such as PL-SQL APIs, tables, views, functions, and procedures. These artifacts are further categorized based on the schema they belong to. So, another use of the artifact-based view is to use artifacts that belong to your schema as well as the artifacts that belong to other schemas. This view also enables you to search for artifacts across all schemas.|  
|**Schema-based view**|This view is categorized by the schemas available in the underlying Oracle database. Use this view when you know which schema has the artifacts you want to work with. Within this view, the artifacts as categorized as PL-SQL APIs, procedures, functions, tables, and views.|  
  
 For more information on how the Oracle E-Business Suite artifacts are categorized, see [Connect to Oracle E-Business Suite in Visual Studio using Add Adapter Metadata Wizard](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-ebs-in-visual-studio-using-add-adapter-metadata-wizard.md) Another key reason for organizing the artifacts in different views is the ease to search for specific artifacts. For more information on how you can search for artifacts, see [Search for Oracle E-Business Suite operations](../../adapters-and-accelerators/adapter-oracle-ebs/search-for-oracle-e-business-suite-operations.md).  
  
> [!IMPORTANT]
>  The nodes show up based on the connection URI you specify while establishing a connection. If you specify credentials that do not have permissions on the Oracle E-Business Suite artifacts, you cannot use the artifacts in the **Application-based view**. Also, the **Artifact-based view** does not list the artifacts belonging to Oracle E-Business Suite.  
  

  
## See Also  
 [Get metadata for Oracle E-Business Suite operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)