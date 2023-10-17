---
description: "Learn more about: Step 5: Build the EAISchemas Project"
title: "Step 5: Build the EAISchemas Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c20cd368-7446-4861-8d71-5bc25ce408a2
caps.latest.revision: 41
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 5: Build the EAISchemas Project
![Step 5 of 5](../core/media/step-5of5.gif "Step_5of5")  
  
 **Time to complete:** 6 minutes  
  
 **Objective:** In this step, you compile the EAISchemas project.  
  
 **Purpose:** The most important aspect of Microsoft BizTalk Server and the .NET Framework is that all BizTalk Server artifacts; maps, schemas, orchestrations, and pipelines, get compiled into .NET assemblies. The two most important implications of this design are that these assemblies must have strong names, and because of that, they also follow .NET versioning rules. The main implication of this is that a BizTalk project, once built against a particular version of another .NET project or assembly (including BizTalk projects), continues to use that version until it has been rebuilt against a newer version.  
  
## Prerequisites  
 Note the following requirements before you begin this step:  
  
-   Before you begin this step you must complete the following steps:  
  
    -   [Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md)  
  
    -   [Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) 
  
    -   [Step 3: Create the Request Decline Schema](../core/step-3-create-the-request-decline-schema.md)  
  
    -   [Step 4: Create the Map](../core/step-4-create-the-map.md)  
  
## Procedures  
  
#### To build the EAISchemas project  
  
1.  In Solution Explorer, right-click **EAISchemas**, and then click **Build**.  
  
     The bottom of the screen should display:  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ```  
  
## What did I just do?  
 In this step, you built the EAISchemas project to generate an assembly file (DLL).  
  
## Next Steps  
 You create the business process that evaluates the contents of the inventory replenishment request message against approval criteria in [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md).  
  
## See Also  
 [Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md)   
 [Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md)   
 [Step 3: Create the Request Decline Schema](../core/step-3-create-the-request-decline-schema.md)   
 [Step 4: Create the Map](../core/step-4-create-the-map.md)
