---
description: "Learn more about: Lesson 4: Perform an Insert Operation on the Purchase Order Table"
title: "Lesson 4: Perform an Insert Operation on the Purchase Order Table"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Lesson 4: Perform an Insert Operation on the Purchase Order Table
In [Lesson 3: Execute a Stored Procedure to Select New Employees Added](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md), you executed the **UPDATE_EMPLOYEE** stored procedure and received a response message that contains the details of the newly inserted employee record. In this lesson, you will build on the previous lesson and update the orchestration to perform the following steps:  
  
1.  Within the orchestration, you build the message to perform an Insert operation on the **Purchase_Order** table. This step is similar to [Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md).  
  
2.  After you build the request message, you map the response message of the **UPDATE_EMPLOYEE** stored procedure to the request message for the Insert operation on the **Purchase_Order** table. By mapping the messages, you pass the values received from the response messages to the request message for Insert operation.  
  
3.  You send the message to insert a record in the **Purchase_Order** table and receive a response.  
  
4.  You send the response to a send port.  
  
## In This Section  
  
-   [Step 1: Create the Request Message for Insert Operation on Purchase_Order Table](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md)  
  
-   [Step 2: Map the UPDATE_EMPLOYEE Response Message to Insert Operation Request Message](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md)  
  
-   [Step 3: Send the Request Message to Insert Records and Receive a Response](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md)  
  
-   [Step 4: Build the Project](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md)
