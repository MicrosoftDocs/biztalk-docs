---
title: "Default Property Schema Name (Schema File Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schema file properties, Default Property Schema Name property"
  - "Default Property Schema Name property [schema file]"
  - "schemas, Quick Promotion feature"
  - "schemas, files"
  - "Quick Promotion feature"
ms.assetid: e53b023e-c5de-450b-9b60-bda0ec5cf16b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Default Property Schema Name (Schema File Property)
Use the **Default Property Schema Name** property to specify the name of the property schema file used by the **Quick Promotion** feature.  
  
## Category  
 Property Schema  
  
## Allowed Values  
 A valid, pathless file name with an .xsd extension that identifies the file to use as the default property schema.  
  
## Default Value  
 PropertySchema.xsd  
  
## Remarks  
 You can examine and set this property in the **Property Pages** dialog box that appears when you right-click a schema file in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer and then click **Properties** on the shortcut menu.  
  
 If the specified file does not exist, it will be created, added to the project, and persisted in the XSD representation of the schema when you use the **Quick Promotion** feature.  
  
 Do not specify a path; only specify a file name with the .xsd extension.  
  
## See Also  
 [Schema File Properties](../core/schema-file-properties.md)