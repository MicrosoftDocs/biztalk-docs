---
title: "How to Start the Business Rule Composer and Load a Policy | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "policies, loading"
  - "opening, Busines Rule Composer"
  - "Business Rule Composer, policies"
  - "Business Rule Composer, opening"
ms.assetid: 34a6034d-90b3-4ce0-9770-3790763affe3
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Start the Business Rule Composer and Load a Policy
This section describes how to start the Business Rule Composer and load a policy.  
  
### To start the Business Rule Composer  
  
- On the **Start** menu, point to **All Programs**, point to Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and then click **Business Rule Composer**.  
  
  > [!NOTE]
  >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
### To load a policy  
  
1.  In the Business Rule Composer, on the **Rule Store** menu, click **Load**.  
  
2.  In the **Rule Store** dialog box, in the **SQL Server** drop-down list, select the SQL Server™ computer to which you want to connect.  
  
3.  In the **Database** drop-down list, select the database that contains the rule store you want to open.  
  
> [!NOTE]
>  The default database for the rule store installed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is **BizTalkRuleEngineDb**.  
> 
> [!NOTE]
>  If you use a newly created SQL Server account that has the **Enforce password expiration** and **User must change password at next login** options set, the business rule composer will fail to connect to the Rule Engine database.