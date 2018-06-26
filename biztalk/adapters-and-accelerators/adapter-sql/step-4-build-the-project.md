---
title: "Step 4: Build the Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d88b1407-ecdd-4dbf-90da-02dc4781568c
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 4: Build the Project
![Step 4 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **Time to complete:** 5 minutes  
  
 **Objective:** In this step, you compile the BizTalk orchestration project.  
  
## Prerequisites  
 You must have completed [Step 3: Send the Request Message to Insert Records and Receive a Response](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md).  
  
### To build the BizTalk orchestration project  
  
1. In the Solution Explorer, right-click the BizTalk project name, and then click **Properties**.  
  
2. In the property pages dialog box, in the tree pane, expand **Common Properties**, click **Assembly**, and then in the properties list, click the **Assembly Key File** ellipsis **[…]**.  
  
3. Specify a path to the assembly key file you created as described in [Prerequisites to create SQL applications using the SQL adapter](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md), and then click **Open**.  
  
4. In the property pages dialog box, in the tree pane, expand **Configuration Properties**, click **Deployment**, and then do the following:  
  
   1. For the **Application Name** property, type `SampleApplication`.  
  
   2. For the **Redeploy** property, select **True**.  
  
      Click **OK**.  
  
5. On the **File** menu, click **Save All**.  
  
6. In Solution Explorer, right-click the solution name, and then click **Build Solution**.  
  
    The Output pane at the bottom of the screen should read: **Build: 3 succeeded or up-to-date, 0 failed, 0 skipped.**  
  
## What did I just do?  
 In this step, you compiled the solution containing the BizTalk project and two class library projects.  
  
## Next Steps  
 You deploy the solution, as described in [Lesson 5: Deploy the Solution](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md).  
  
## See Also  
 [Step 3: Send the Request Message to Insert Records and Receive a Response](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md)   
 [Lesson 4: Perform an Insert Operation on the Purchase Order Table](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)