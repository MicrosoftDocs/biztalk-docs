---
title: "Step 3: Test the Solution2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30dbc7c9-3c5f-4953-b26f-5c41141c22ad
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Test the Solution
![Step 3 of 3](../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **Time to complete:** 5 minutes  
  
 **Objective:** In this step, you test how the EAI solution processes messages.  
  
 **Purpose:** In this step, you check that the EAIProcess orchestration processes messages correctly. You do this by dropping sample messages into the receive location specified for the EAI application. If the EAI solution is working properly, if the EAIProcess orchestration receives a message from the warehouse requesting more than 500 items, the orchestration generates a decline request message. If the EAIProcess orchestration receives a message from the warehouse requesting fewer than 500 items, the orchestration passes the message on to the ERP system.  
  
## Prerequisites  
 Before you begin this step you must complete [Step 2: Configure and Start the Application](../core/step-2-configure-and-start-the-application1.md).  
  
## Procedures  
  
#### To test the EAI solution  
  
1.  Open Windows Explorer, and navigate to **C:\BTSTutorials\WareHouse**.  This folder is created by installing the tutorial files.  
  
2.  Copy **RequestInstance.XML** and paste it into **C:\BTSTutorials\WareHouse\Request**.  
  
3.  When the file disappears, check **C:\BTSTutorials\ERP\Request**.  
  
4.  In Windows Explorer, navigate to **C:\BTSTutorials\WareHouse**.  
  
5.  Copy **RequestInstance(Over Limit).XML** and paste it into **C:\BTSTutorials\WareHouse\Request**.  
  
6.  When the file disappears, check **C:\BTSTutorials\WareHouse\RequestDecline**.  
  
## What did I just do?  
 You tested the EAI solution by placing sample messages in the receive location for the EAI application.  
  
## See Also  
 [Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md)   
 [Step 2: Configure and Start the Application](../core/step-2-configure-and-start-the-application1.md)