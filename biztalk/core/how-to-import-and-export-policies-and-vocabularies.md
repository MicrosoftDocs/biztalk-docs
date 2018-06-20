---
title: "How to Import and Export Policies and Vocabularies | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "policies, exporting"
  - "Rule Engine Deployment Wizard"
  - "policies, importing"
  - "vocabularies, exporting"
  - "vocabularies, importing"
ms.assetid: c427f686-5908-4f72-9e72-46a5497274ac
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Import and Export Policies and Vocabularies
You can use the Rules Engine Deployment Wizard to import or export a policy or vocabulary.  

> [!NOTE]
>  All vocabularies used by a policy or vocabulary must be imported first or you will get an error.  

### To import or export a policy or vocabulary  

1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rules Engine Deployment Wizard**.  

   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  

2. On the welcome page, click **Next**.  

3. On the **Deployment Task** page, select either **Export Policy/Vocabulary to file from database** or **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.  

4. On the **Policy Store** page, from the drop-down lists, select an available SQL Server computer and database, and then click **Next**.  

5. On the **Export Policy/Vocabulary** page, do the following, and then click **Next**.  

   1.  Select **Policy** or **Vocabulary** depending on what you want to export/import.  

   2.  From the **Policy/Vocabulary** drop-down list, select the desired policy/vocabulary.  

   3.  Click **Browse** to select the definition file.  

6. Review the server, database, and policy or vocabulary information, and then click **Next**.  

7. After the import or export is completed, click **Next**.  

8. Review the completion status of the import or export, and then click **Finish**.
