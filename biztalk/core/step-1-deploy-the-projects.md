---
title: "Step 1: Deploy the Projects | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0467c140-1f4c-4cfa-b46f-dc1d0f8755d4
caps.latest.revision: 44
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Deploy the Projects
![Step 1 of 3](../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **Time to complete:** 5 minutes  
  
 **Objective:** In this step, you deploy the EAISchemas and EAIOrchestration projects.  
  
 **Purpose:** When you deploy a project or solution in Visual Studio, the assemblies are automatically built and deployed into the specified application. As part of this process, the assembly along with the orchestrations, schemas, and maps that it contains (called "artifacts") are imported into the local BizTalk Management database and associated in the database with the specified application.  
  
## Prerequisites  
  
- [Lesson 1: Define Schemas and a Map](../core/lesson-1-define-schemas-and-a-map.md)  
  
- [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md)  
  
- Sign in as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group

- Run Visual Studio with Administrative privileges

> [!TIP]
> You can download the required tutorial files at [Tutorial 1: Enterprise Application Integration](https://www.microsoft.com/download/details.aspx?id=22793).

## Open the solution with administrative rights  
  
1. Sign in to Windows as a member of the BizTalk Server Administrators group.  
  
2. Start **Microsoft Visual Studio** as an administrator.  
  
3. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **Open**, and then click **Project/Solution**.  
  
4. In the **Open Project** dialog box, browse to the **EAISolution.sln** project solution file, and then click **Open**.  
  
   The deployment process requires that assembly is strongly signed.  You must sign your assemblies by associating the project with a strong name assembly key file.  This file is included in the tutorial files.  
  
   The BizTalk application is a feature of BizTalk Server that makes it quicker and easier to deploy, manage, and troubleshoot BizTalk Server business solutions. A BizTalk application is a logical grouping of the items, called "artifacts," used in a BizTalk Server business solution. We can specify an application name for a project.  The deployment process automatically creates a new application having the specified name if it doesn’t exist.  
  
## Configure and deploy the projects  
  
1.  In Solution Explorer, right-click the **EAISchemas** project, and then click **Properties**.  
  
2.  Click the **Signing** tab, select **Sign the assembly**.  
  
3.  From the drop-down list in the **Choose a strong name key file** box, select **\<Browse…\>**.  
  
4.  In the **Select File** dialog box, navigate to **C:\BTStutorials**, click **btsTutorials.snk**, and then click **Open**. 
  
5.  Click the **Deployment** tab, in the box to the right of **Application Name**, type `EAISolution`.  
  
6.  From the drop-down list in the box to the right of **Redeploy**, select **True**.  
  
7.  In Solution Explorer, right-click **EAISchemas**, and then click **Deploy**.  The Output window should display:  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ========== Deploy: 1 succeeded, 0 failed, 0 skipped ==========  
  
    ```  
  
8.  Repeat steps 1 through 7 to deploy the EAIOrchestration project.  
  
## What did I just do?  
 In this step, you deployed the EAISchemas and EAIOrchestration projects.  
  
## Next Steps  
 You create the physical ports, and bind them to the logical ports of the orchestration.  
  
 [Step 2: Configure and Start the Application](../core/step-2-configure-and-start-the-application1.md)   
 [Step 3: Test the Solution](../core/step-3-test-the-solution2.md)
