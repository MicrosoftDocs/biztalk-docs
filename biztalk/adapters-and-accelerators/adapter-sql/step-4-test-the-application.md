---
description: "Learn more about: Step 4: Test the Application"
title: "Step 4: Test the Application"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 4: Test the Application
![Step 4 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **Time to complete:** 10 minutes  
  
 **Objective:** In this step, you test the application by inserting a record in the **Employee** table of the **ADAPTER_SAMPLES** database. If the application is working properly, the orchestration receives a notification for changes to the **Employee** table. The orchestration then extracts the type of notification received. If the notification is for an Insert operation, the orchestration executes the **UPDATE_EMPLOYEE** stored procedure and receives a response. The orchestration extracts the values of **Employee_ID** and **Name** from the response and inserts them into the **Purchase_Order** table.  
  
## Prerequisites  
 Before starting with this step, you must ensure the following:  
  
-   A request message to invoke the **UPDATE_EMPLOYEE** stored procedure is available at C:\TestLocation\CreateEmployeeMessage. The request message looks like the following:  
  
    ```  
    <UPDATE_EMPLOYEE xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/dbo" />  
    ```  
  
-   A request message to invoke the Insert operation on the **Purchase_Order** table is available at C:\TestLocation\CreatePOMessage. The request message looks like the following:  
  
    ```  
    <Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Purchase_Order">  
      <Rows>  
        <Purchase_Order xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
          <Employee_ID>10</Employee_ID><Employee_Name>Employee_Name</Employee_Name>  
        </Purchase_Order>  
      </Rows>  
    </Insert>  
    ```  
  
    > [!NOTE]
    >  The values for the **Employee_ID** and **Employee_Name** fields are placeholders. The actual values are inserted by the orchestration at run-time.  
  
-   You must have completed [Step 3: Configure and Start the Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md).  
  
### To test the application  
  
1.  Insert a record in the **Employee** table. You can do so by running the following statement from SQL Server Management Studio.  
  
    ```  
    INSERT INTO [ADAPTER_SAMPLES].[dbo].[Employee] ([Name] ,[Designation] ,[Salary])  
    VALUES('John Smith' ,'Manager' ,500000)  
    ```  
  
2.  Check the **Employee** table in the database. You will notice that the new record is added by the **Status** column is “0.”  
  
3.  Keep refreshing the **Employee** table records. You will notice that the **Status** column for the new record is now set to “1.”  
  
4.  Check the **Purchase_Order** table. You will notice that a record with the same employee name and designation, as you provided in the Insert statement, is added to the table.  
  
5.  If you provided your e-mail alias in the SMTP port configuration, you will also receive an e-mail with the response message for the Insert operation.  
  
## What did I just do?  
 Tested the SampleApplication application by inserting a record in the **Employee** table.  
  
## Next Steps  
 If the test worked, congratulations! You have completed the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] tutorial.  
  
 If the test did not work, carefully check your work to make sure that you added all of the necessary objects and set their properties correctly.  
  
## See Also  
 [Step 3: Configure and Start the Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md)   
 [Lesson 5: Deploy the Solution](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)
