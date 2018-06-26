---
title: "Lesson 3: Execute a Stored Procedure to Select New Employees Added | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec7897e9-0c77-41b2-8cc2-61745bd3b028
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 3: Execute a Stored Procedure to Select New Employees Added
Before understanding the tasks performed in this lesson, you must first understand why these tasks are required. The **Employee** table to which the records are inserted to add a new employee is defined in such a way that a **Status** column is always set to “0” every time a new employee is added. This is done so that you can use this column to query for newly added employees and also get notifications. In SQL Server, you would query this by running the following SQL statement:  
  
```  
SELECT Employee_ID, Name, Designation FROM Employee WHERE Status = 0  
```  
  
 After receiving the list of newly added employees, you must also update the **Status** column to “1” so that the next time new employees are added and you run the same query, you do not get records for old employees as well. To make sure that the above Select statement gives only the newly added employees, you will update the **Employee** table using the following SQL statement:  
  
```  
UPDATE Employee SET Status = 1 WHERE Status = 0  
```  
  
 So, the **Status** column for the old employees is set to “1” while new employees will always be “0.”  
  
 In this lesson, you will execute a stored procedure, **UPDATE_EMPLOYEE**, which in turn executes the Select and Update statements. After you have finished this lesson, your orchestration will do the following:  
  
1. Receives notification for any changes to the **Employee** table.  
  
2. Extracts the type of notification from the notification message received.  
  
3. If the notification message is for an Insert operation, the orchestration executes the **UPDATE_EMPLOYEE** stored procedure.  
  
4. The stored procedure reads the newly entered records in the **Employee** table. After reading the new records, the stored procedure also sets the **Status** column for those records to “1.”  
  
   Now you know why you need to execute the stored procedure. You now need to think about how to execute this as part of the orchestration. The orchestration needs a request message for the **UPDATE_EMPLOYEE** stored procedure. In this tutorial, you will create a custom class library that will create the message on the fly and then provide it to the orchestration. After the orchestration receives the message, it will send the message to the SQL Server using the SQL adapter and receive the response.  
  
## In This Section  
  
-   [Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)  
  
-   [Step 2: Send the Request Message to SQL Server and Receive Response](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md)