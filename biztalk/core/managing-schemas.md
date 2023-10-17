---
title: "Manage schemas | Microsoft Docs"
description: Use BizTalk Administration to work with schemas in BizTalk Server, including showing and hiding properties, view the XSD, enable tracking
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5632e79-b182-41c9-9138-eb88b44e3172
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Manage Schemas

## Overiew
This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to manage schemas. Schemas are used by pipelines and orchestrations to represent the message that will be processed.  
  
 Schemas are created in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and compiled into BizTalk assemblies. You cannot add a schema to an application individually; a schema is added to an application as follows:  
  
- When you add a BizTalk assembly containing a schema to the application, as described in [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
- When you import an .msi file into an application that includes a BizTalk assembly containing a schema, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).  
  
- When a developer deploys into an application an assembly containing a schema from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  
  
  For background information about schemas, see [Schemas](../core/schemas.md). For information about developing schemas, see [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md).  
  
> [!NOTE]
>  You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## Next steps 
  
-   [Show and Hide Property Schemas](../core/how-to-show-and-hide-property-schemas.md)  
  
-   [View the Schema Definition (XSD) of a Schema](../core/how-to-view-the-schema-definition-xsd-of-a-schema.md)  
  
-   [Configure Tracking for a Schema](../core/how-to-configure-tracking-for-a-schema.md)  
  
-   [Remove a Schema from an Application](../core/how-to-remove-a-schema-from-an-application.md)