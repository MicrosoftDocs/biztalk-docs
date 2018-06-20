---
title: "Validating the Adapter Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8eeb8742-7083-462b-8d3a-e58103112542
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Validating the Adapter Configuration
While adding the receive location and send port, you will be asked to configure your custom properties in the **\<**<em>Adapter Name</em>**\> Transport Properties** dialog box. The XSD schema files in the AdapterHarness project define these properties.  
  
 Validation of the configuration schema occurs in three parts:  
  
1.  When displaying a saved configuration, the Adapter Framework validates the saved XML document against the schema before loading the document into the property page. The framework assumes that a document that is not valid indicates a change in the configuration schema definition. Only valid documents get loaded into the property page.  
  
2.  When saving a configuration, if the adapter implements the **IAdapterConfigValidation** interface, the framework passes to the adapter the XML document constructed from serializing the property page data. The adapter then processes the document. Any errors should produce exceptions that are caught by the framework and displayed to the user. Any missing or generated values should be generated during validation. Using the \<browsable show="false"\> decoration suppresses showing an entry in the property grid, even though the value appears in the XML instance.  
  
3.  When saving a configuration before placing the value into the database, the framework again validates the XML document against the schema. This ensures that only valid data is persisted.  
  
## See Also  
 [Adapter Design Issues](../core/adapter-design-issues.md)