---
title: "Add Adapter Metadata Wizard Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.add.wizard.dialog"
helpviewer_keywords: 
  - "projects, adapters"
  - "adapters, schemas"
  - "schemas, projects [adapters]"
  - "adapters, projects"
  - "projects, schemas [adapters]"
  - "schemas, adapters"
ms.assetid: 0108026c-33cd-4b93-a086-24a6948c11bd
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Add Adapter Metadata Wizard Dialog Box
Use the **Add Adapter Metadata Wizard** to add adapter schemas to your BizTalk project.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Adapter**|Select the name of the adapter that contains the adapter schemas to add to the project.|  
|**SQL Server**|Type the BizTalk database name or select it from the drop-down list.<br /><br /> This property is optional. If left blank, you must configure it later in BizTalk Explorer.|  
|**Database**|Select the BizTalk Management database for the chosen server.<br /><br /> This property is optional. If left blank, you must configure it later in BizTalk Explorer. **Note:**  The BizTalk Management database is also referred to as the BizTalk Configuration database.|  
|**Port**|Displays the list of adapter send ports and receive locations previously created and stored in the BizTalk Management database for the adapter selected. If selected, this port appears in the Connection Stringbox on the next page in the wizard.<br /><br /> This property is optional. If left blank, you may later need to configure a send port or receive location in BizTalk Explorer.|  
  
## See Also  
 [How to Add Adapter Metadata to a BizTalk Project](../core/how-to-add-adapter-metadata-to-a-biztalk-project.md)