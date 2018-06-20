---
title: "Step 2: Create Messages for BizTalk Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47a4fb98-6085-4aeb-ab39-2f2c3858d4e0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Create Messages for BizTalk Orchestrations
![Step 2 of 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")  
  
 **Time to complete:** 5 minutes  
  
 **Objective:** In this step, you add an orchestration to the BizTalk project and create messages for the schemas you generated in [Step 1: Generate Schema for Operations](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md).  
  
## Prerequisites  
 You must have completed [Step 1: Generate Schema for Operations](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md).  
  
### To create messages in an orchestration  
  
1. Add a BizTalk orchestration to the BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]:  
  
   1.  From Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**.  
  
   2.  In the **Add New Item** dialog box, from the **Categories** box, click **Orchestration Files**. From the **Templates** box, click **BizTalk Orchestration**.  
  
   3.  Type a name for the BizTalk orchestration, and then click **Add**. For this tutorial, enter the name `EmployeeOrch.odx`.  
  
2. Open the **Orchestration View** window of the BizTalk project, if it is not already open. To do so, click **View**, point to **Other Windows**, and then click **Orchestration View**.  
  
3. Add messages to the orchestration.  
  
   1.  In the **Orchestration View**, right-click **Messages**, and then click **New Message**.  
  
   2.  Right-click the newly created message, and then select **Properties Window**.  
  
   3.  In the **Properties** pane for **Message_1**, do the following:  
  
       |Use this|To do this|  
       |--------------|----------------|  
       |Identifier|Type `NotifyReceive`.|  
       |Message Type|From the drop-down list, expand **Schemas**, and select **Employee_PurchaseOrder.Notification**, where Employee_PurchaseOrder is the name of your BizTalk project. Notification is the schema generated for the **Notification** operation.|  
  
   4.  Repeat the previous step to add four new messages—a request-response message set for invoking the UPDATE_EMPLOYEE stored procedure and another request-response message set for performing the **Insert** operation on **Purchase_Order** table.  
  
       |Set Identifier to|Set Message Type to|  
       |-----------------------|-------------------------|  
       |UpdateEmployee|*Employee_PurchaseOrder.TypedProcedure_dbo.UPDATE_EMPLOYEE*, where TypedProcedure_dbo.UPDATE_EMPLOYEE is the schema for the UPDATE_EMPLOYEE stored procedure.|  
       |UpdateEmployeeResponse|*Employee_PurchaseOrder.TypedProcedure_dbo.UPDATE_EMPLOYEEResponse*|  
       |InsertPO|*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.Insert*, where TableOperation_dbo_Purchase_Order.Insert is the schema for the Insert operation on the Purchase_Order table.|  
       |InsertPOResponse|*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.InsertResponse*|  
  
   5.  Save the orchestration file and the BizTalk project.  
  
## What did I just do?  
 In this step, you created messages for invoking performing inbound and outbound operations on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## Next Steps  
 You add orchestration shapes to receive notification from SQL Server and filter notifications for Insert operation, as described in [Lesson 2: Receive and Filter Notifications](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md).  
  
## See Also  
 [Lesson 1: Generate Schemas and Create Messages](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)   
 [Step 1: Generate Schema for Operations](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md)