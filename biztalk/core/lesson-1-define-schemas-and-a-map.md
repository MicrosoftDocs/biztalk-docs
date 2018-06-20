---
title: "Lesson 1: Define Schemas and a Map | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "enterprise application integration tutorial, creating solutions"
ms.assetid: 4fe7720d-722e-4fa0-a556-477fc66ffa12
caps.latest.revision: 35
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 1: Define Schemas and a Map
In this lesson, you create and build the first project in the enterprise application integration (EAI) solution. The project contains two message schemas, and a map.  
  
 In the EAI solution, a warehouse system sends a request message for inventory replenishment to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for processing. In this lesson, you create the following items:  
  
- The EAI solution, to hold the project.  
  
- The project, to hold the schemas and the map.  
  
- The schema, for the message the warehouse sends to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to request inventory replenishment.  
  
- The schema, for the message that the warehouse is expecting when a request is rejected.  
  
- A map, for reformatting a request message to create a request decline message.  
  
  Finally you build the project before starting [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md). In Lesson 2, you create the business process that routes the messages and evaluates the contents of the inventory replenishment request message against approval criteria.  
  
## In This Section  
  
-   [Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md)  
  
-   [Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md)  
  
-   [Step 3: Create the Request Decline Schema](../core/step-3-create-the-request-decline-schema.md)  
  
-   [Step 4: Create the Map](../core/step-4-create-the-map.md)  
  
-   [Step 5: Build the EAISchemas Project](../core/step-5-build-the-eaischemas-project.md)  
  
## See Also  
 [Before You Begin the Tutorial](../core/before-you-begin-the-tutorial.md)   
 [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md)   
 [Lesson 3: Deploy the Solution](../core/lesson-3-deploy-the-solution.md)