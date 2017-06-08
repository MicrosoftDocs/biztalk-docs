---
title: "Customizing Binding Files | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, binding files"
  - "binding files"
  - "binding files, about binding files"
  - "binding files, customizing"
ms.assetid: 4714e6c2-4912-43aa-ba5a-0be06916a30a
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Customizing Binding Files
Binding files are XML files that describe artifacts in a BizTalk Management database and the relationship between these artifacts. Binding files are useful for exporting configuration information from one BizTalk configuration database and importing this information into another BizTalk configuration database. For example, a developer may design a BizTalk solution and its related artifacts in a development environment, then export these artifacts to a binding file and finally, import these artifacts into a production environment. You can also use a binding file to update an existing configuration. For example you can apply configuration changes made in a development environment to your production environment with a binding file. This topic discusses considerations when updating an existing configuration with a binding file, the structure of a binding file, and adapter specific configuration properties that can be set in a binding file.  
  
## In This Section  
  
-   [Updating an Existing Configuration with a Binding File](../core/updating-an-existing-configuration-with-a-binding-file.md)  
  
-   [Structure of a Binding File](../core/structure-of-a-binding-file.md)  
  
-   [Configuration Properties for Integrated BizTalk Adapters](../core/configuration-properties-for-integrated-biztalk-adapters.md)