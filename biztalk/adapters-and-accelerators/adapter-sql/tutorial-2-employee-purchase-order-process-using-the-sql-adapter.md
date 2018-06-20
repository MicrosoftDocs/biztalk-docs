---
title: "Tutorial 2: Employee - Purchase Order Process using the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eeb4dd1e-209a-47eb-9c0e-a138e02f0ff2
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tutorial 2: Employee - Purchase Order Process using the SQL adapter
In this tutorial, you are automating the process where the Purchases department that places an equipment order every time a new employee joins the organization. Both employee details and purchase order details are maintained in **Employee** and **Purchase_Order** tables respectively, in a SQL Server database. The Purchases department is informed by updating the Purchase_Order table in the SQL Server database and by sending an e-mail. Within the process, the following actions occur:  
  
1. The adapter receives a notification each time the **Employee** table is updated. The adapter then sends a notification to the BizTalk orchestration.  
  
2. The BizTalk orchestration figures out whether the notification is for a new record inserted into the **Employee** table. If the notification is for any other operation on the **Employee** table, the orchestration does not perform any operation.  
  
3. If the notification is for an Insert operation on the **Employee** table, notifying that a new employee record was added, the orchestration uses the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to read the details of the new record.  
  
4. The orchestration receives a response that contains the details of the new added employee record. The orchestration maps the **Employee_ID** and **Designation** fields in the response to the request message for the Insert operation on the **Purchase_Order** table.  
  
5. The orchestration then uses the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to perform an Insert operation on the **Purchase_Order** table. The response for the Insert operation is sent to the Purchases department as an e-mail.  
  
## About the Database Objects Used in this Sample  
 This tutorial uses the database objects created by the SQL script shipped with the samples. For more information about the script and the samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md). The database objects that you will use in this tutorial are:  
  
- **ADAPTER_SAMPLES** database.  
  
- **Employee** and **Purchase_Order** tables.  
  
- **UPDATE_EMPLOYEE** stored procedure.  
  
  All these database objects are created when you run the SQL script provided with the sample. Make sure you run the script before you start with the tutorial.  
  
## Sample Based on This Tutorial  
 A sample, **Employee_PurchaseOrder**, which is based on this tutorial is also provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
 We recommend that you go through the tutorial completely to understand how to create BizTalk projects using the adapter, and then look at the sample as a reference.  
  
## In This Section  
  
-   [Lesson 1: Generate Schemas and Create Messages](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)  
  
-   [Lesson 2: Receive and Filter Notifications](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)  
  
-   [Lesson 3: Execute a Stored Procedure to Select New Employees Added](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)  
  
-   [Lesson 4: Perform an Insert Operation on the Purchase Order Table](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)  
  
-   [Lesson 5: Deploy the Solution](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)