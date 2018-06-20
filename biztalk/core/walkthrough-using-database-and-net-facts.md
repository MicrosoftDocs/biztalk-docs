---
title: "Walkthrough: Using Database and .NET Facts | Microsoft Docs"
ms.custom: ""
ms.date: "2016-04-05"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 676d6e46-d9f8-477e-979e-1ac051ad4451
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Using Database and .NET Facts
This walkthrough provides step-by-step procedures for using the Business Rule Composer to create a policy that uses database and .NET facts.  

## Prerequisites  
 You must set the value of the **StaticSupport** registry key to 1 or 2 before performing the walkthrough. This allows the policy to invoke the static methods of a .NET class without requiring the client to assert an instance of the class. For more information, see [Invoking Static Members of a Class](../core/invoking-static-members-of-a-class.md).  

## Overview of This Walkthrough  
 This walkthrough contains five procedures, as described in the following table.  

|Procedure title|Procedure description|  
|---------------------|---------------------------|  
|To create the TestDB database and the PO table|Provides step-by-step instructions for creating the **TestDB** database and the **PO** table.|  
|To create the POUtility component|Provides step-by-step instructions for creating the **POUtility** component.|  
|To create the ProcessPurchaseOrderDbNet business policy|Provides step-by-step instructions for creating the **ProcessPurchaseOrderDbNet** policy.|  
|To test the ProcessPurchaseOrderDbNet policy by using the Business Rule Composer|Provides step-by-step instructions for using the Business Rule Composer to test the **ProcessPurchaseOrderDbNet** policy.|  
|To test the ProcessPurchaseOrderDbNet policy by using the Policy.Execute method|Provides step-by-step instructions for testing the **ProcessPurchaseOrderDbNet** policy by using the **Policy.Execute** method.|  

### To create the TestDB database and the PO table  

1.  Open **SQL Server Management Studio**.  

2.  Verify the server name and authentication, and then click **Connect**.  

3.  In the Object Explorer window on the left, right-click the computer name, and then click **New Query**.  

4.  Copy the following SQL statements to the query window:  

    ```  
    CREATE DATABASE [TestDB]  
    GO  

    Use TestDB  
    CREATE TABLE [dbo].[PO]([PONumber] [nvarchar](50) NOT NULL,  
    [Quantity] [int] NOT NULL,  
    [Status] [nchar](10) NULL  
    CONSTRAINT [PK_PO] PRIMARY KEY CLUSTERED ([PONumber] ASC))   
    GO  

    INSERT INTO PO VALUES ('PO1', 400, NULL)  
    INSERT INTO PO VALUES ('PO2', 700, NULL)  
    GO  
    ```  

5.  Press F5 to execute the SQL query.  

6.  In the Object Explorer window, expand the computer name, expand **Databases**, and then verify that **TestDB** exists.  

7.  Expand **TestDB**, expand **Tables**, and then verify that **dbo.PO** exists.  

8.  Right-click **dbo.PO**, and then click **Open Table** to verify that the following data exists in the table.  

    |PONumber|Quantity|Status|  
    |--------------|--------------|------------|  
    |PO1|400|NULL|  
    |PO2|700|NULL|  

### To create the POUtility component  

1. Start **Microsoft Visual Studio**.  

2. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.  

3. In the **New Project** dialog box, do the following:  


   |             Use this              |                             To do this                              |
   |-----------------------------------|---------------------------------------------------------------------|
   |         **Project types**         |                        Click **Visual C#**.                         |
   |           **Templates**           |                      Click **Class Library**.                       |
   |             **Name**              |                       Type **POUtilityLib**.                        |
   |           **Location**            |          Specify **C:\BRE-Walkthroughs** as the location.           |
   |         **Solution Name**         |                       Type **POUtilitySol**.                        |
   | **Create directory for solution** | Select this check box to create a directory for the solution files. |


4. Click **OK**. The **POUtilityLib** project should appear in Solution Explorer. If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.  

5. In the Properties window, change the name of the file, **Class1.cs**, to **POUtility.cs**.  

6. Add a public constructor to the class as shown in the following code:  

   ```  
   public POUtility()  
   {  
   }  
   ```  

7. Add a static method named **GetMaxAllowed** to the **POUtility** class as shown in the following code:  

   ```  
   public static int GetMaxAllowed()  
   {  
   return 500;  
   }   
   ```  

8. Start **Visual Studio Command Prompt**.  

9. Change the directory to **C:\BRE-Walkthroughs\POUtilitySol**, and then execute the following command:  

     **Sn -k POUtility.snk**  

10. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, expand **Properties**, and then double-click **AssemblyInfo.cs**.  

11. Add the following statement to the **AssemblyInfo.cs** file at the end:  

    ```  
    [assembly: AssemblyKeyFile(@"C:\BRE-Walkthroughs\POUtilitySol\POUtility.snk")]  
    ```  

12. In the Solution Explorer window, right-click **POUtilityLib**, and then click **Build**.  

13. At the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt, change the directory to **C:\BRE-Walkthroughs\POUtilitySol\POUtilityLib\Bin\Debug**, and then execute the following command to register the POUtility component with the GAC (global assembly cache). If you do not have the command prompt open, follow step 8 to open it.  

     **Gacutil -i POUtilityLib.dll**  

### To create the ProcessPurchaseOrderDbNet business policy  

1.  On the **Start** menu, open **Business Rule Composer**. If you have the Business Rule Composer already open, press F5 to refresh it.  

    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  

2.  In the Facts Explorer window, click **Databases**.  

3.  Right-click **Servers**, and then click **Browse**.  

4.  Verify the server and authentication information, and then click **OK**.  

5.  Expand **TestDB**, and then expand **PO**.  

6.  In the Facts Explorer window, click **.NET Classes**.  

7.  Right-click **.NETAssemblies**, and then click **Browse**.  

8.  Select **POUtility**, and then click **OK**.  

9. Expand **Class1**.  

10. In the Policy Explorer window, right-click **Policies**, and then click **Add New Policy**.  

11. Change the name of the policy from **Policy1** to **ProcessPurchaseOrderDbNet** and then press ENTER. You can also change the name of the policy in the Properties window.  

12. Right-click **Version 1.0**, and then click **AddNewRule**.  

13. Change the name of the rule from **Rule1** to **ApprovalRule** and then press ENTER. You can also change the name of the rule in the Properties window.  

14. In the IF pane (top) on the right, right-click **Conditions**, click **Predicates**, and then click **LessThanEqual**.  

15. In the Facts Explorer window, click **Databases**.  

16. Drag the **Quantity** node from the Facts Explorer window to **argument1** in the IF pane.  

17. In the Facts Explorer window, click **.NET Classes**.  

18. Drag **GetMaxAllowed** node from the Facts Explorer window to **argument2** in the IF pane.  

19. In the Facts Explorer window, click **Databases**.  

20. Drag the **Status** node from the Facts Explorer window to the THEN pane at the bottom right of the Business Rule Composer.  

21. In the THEN pane, click **\<Enter a value\>** and then type **Approved**.  

22. In the Facts Explorer window, right-click **Version 1.0** in **ProcessPurchaseOrderDbNet**, and then click **AddNewRule**.  

23. Change the name of the rule from **Rule1** to **DeniedRule** and then press ENTER. You can also change the name of the rule in the Properties window.  

24. In the IF pane (top) on the right, right-click **Conditions**, click **Predicates**, and then click **GreaterThan**.  

25. In the Facts Explorer window, click **Databases**.  

26. Drag the **Quantity** node from the Facts Explorer window to **argument1** in the IF pane.  

27. In the Facts Explorer window, click **.NET Classes**.  

28. Drag the **GetMaxAllowed** node from the Facts Explorer window to **argument2** in the IF pane.  

29. In the Facts Explorer window, click **Databases**.  

30. Drag the **Status** node from the Facts Explorer window to the THEN pane at the bottom right of the Business Rule Composer.  

31. In the THEN pane, click **\<Enter a value\>** and then type **Denied**.  

32. In the Policy Explorer window, right-click **Version 1.0 (not saved)**, and then click **Save**.  

### To test the ProcessPurchaseOrderDbNet policy by using the Business Rule Composer  

1.  On the **Start** menu, open **Business Rule Composer**. If you have the Business Rule Composer already open, press F5 to refresh it.  

2.  In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrderDbNet**, right-click **Version 1.0**, and then click **Test Policy**.  

3.  Click **TestDB:PO (Data Connection)**, and then click **Add Instance**.  

4.  In the **Connect to SQL Server** dialog box, verify the server name and authentication information, and then click **OK**.  

5.  In the **Select Binding** dialog box, expand **TestDB**, click **PO**, and then click **OK**.  

6.  Click **Test**.  

7.  In the Output window, verify that both the **ApprovalRule** and the **DeniedRule** are fired.  

8.  In SQL Server Management Studio, right-click **dbo.PO**, and then click **Open Table**.  

9. Verify that the value of the **Status** field is set to **Approved** for the first record.  

10. Verify that the value of the **Status** field is set to **Denied** for the second record.  

    > [!NOTE]
    >  If you still see the value of the **Status** field as NULL, right-click the list containing the data, and then click **Execute SQL**, which refreshes the view.  

11. Keep SQL Server Management Studio open.  

### To test the ProcessPurchaseOrderDbNet policy by using the Policy.Execute method  

1. Start **Microsoft Visual Studio**.  

2. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.  

3. In the **New Project** dialog box, do the following:  


   |             Use this              |                             To do this                              |
   |-----------------------------------|---------------------------------------------------------------------|
   |         **Project types**         |                        Click **Visual C#**.                         |
   |           **Templates**           |                   Click **Console Application**.                    |
   |             **Name**              |                    Type **TestProcessPODbNet**.                     |
   |           **Location**            |          Specify **C:\BRE-Walkthroughs** as the location.           |
   |         **Solution Name**         |                   Type **TestProcessPODbNetSol**.                   |
   | **Create directory for solution** | Select this check box to create a directory for the solution files. |


4. Click **OK**. The **TestProcessPODbNet** project should appear in Solution Explorer. If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.  

5. In Solution Explorer, right-click **References**, and then click **Add Reference**.  

6. Click **Browse**, browse to **\Program Files\Common Files\Microsoft BizTalk**, and then double-click **Microsoft.RuleEngine.dll**.  

7. Add the following code to the top of the **Program.cs** file after the existing `using` statements:  

   ```  
   //To use the SQLConnection class  
   using System.Data.SqlClient;  

   //To use the Policy and DataConnection classes  
   using Microsoft.RuleEngine;  
   ```  

8. Add the following code to the **Main** function to create and open a **SQLConnection** object:  

   ```  
   SqlConnection cn = new SqlConnection("Data Source=(local);Initial Catalog=TestDB;Integrated Security=SSPI");  
   cn.Open();  
   ```  

9. Add the following code to the **Main** function at the end to create a **DataConnection** object based on the **SQLConnection** object you created in the previous step:  

    ```  
    DataConnection dc = new DataConnection("TestDB", "PO", cn);  
    ```  

10. Add the following code to the **Main** function at the end to create a **Policy** object and execute the policy:  

    ```  
    Policy policy = new Policy("ProcessPurchaseOrderDbNet");  
    policy.Execute(dc);  
    ```  

11. Add the following code to the **Main** function at the end to update the database:  

    ```  
    dc.Update();  
    ```  

12. Add the following code to the **Main** function at the end to close the connection to the database:  

    ```  
    cn.Close();  
    ```  

13. Add a try-catch block to catch any exception generated in the **Main** method.  

14. Verify that the complete code for the **Main** function is as shown in the following code:  

    ```  
    try  
    {  
    SqlConnection cn = new SqlConnection("Data Source=(local);Initial Catalog=TestDB;Integrated Security=SSPI");  
    cn.Open();  
    DataConnection dc = new DataConnection("TestDB", "PO", cn);  
    Policy policy = new Policy("ProcessPurchaseOrderDbNet");  
    policy.Execute(dc);  
    dc.Update();  
    cn.Close();  
    }  
    catch (Exception ex)  
    {  
    Console.WriteLine(ex.Message);  
    }  
    ```  

15. On the **Build** menu, click **Build TestProcessPODbNet**.  

16. In the Business Rule Composer, expand **Policies**, expand **ProcessPurchaseOrderDbNet**, right-click **Version 1.0**, and then click **Publish**.  

17. Right-click **Version 1.0 - Published**, and then click **Deploy**.  

18. In SQL Server Management Studio, set the value of the **Status** field to **NULL** for both the PO records.  

19. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], Press CTRL+F5 to execute the **TestProcessPODbNet** application.  

20. Press any key to close the command prompt window.  

21. In SQL Server Management Studio, right-click the table with PO records, and then click **Execute SQL**.  

22. Verify that the value of the **Status** field is set to **Approved** for the first record.  

23. Verify that the value of the **Status** field is set to **Denied** for the second record.  

## Comments  

-   If a policy uses the non-static methods of a .NET class, you need to use a fact creator component that asserts an instance of the .NET class to test the policy by using the Business Rule Composer.  

-   It is very important to remember that the Business Rule Composer creates an instance of the **DataConnection** object and asserts it into the working memory of the rule engine automatically for you. However, when you invoke the policy from a client (BizTalk or non-BizTalk) application, the **DataConnection** object is not created automatically for you. The client should create a **DataConnection** object and pass it as a parameter or fact to the rule engine to execute the policy.  

-   You can use the **DebugTrackingInterceptor** class to track the policy execution details. The following sample code shows how to create an instance of the **DebugTrackingInterceptor** class, and use it when executing the policy:  

    ```  
    DebugTrackingInterceptor dti = new DebugTrackingInterceptor("c:\\Trace.txt");  
    policy.Execute(dc, dti);  
    ```  

-   You can use the **SqlTransaction** class to update the database from the **ProcessPODbNet** policy in a transactional manner. The following code shows how to begin a transaction, pass the transaction as a parameter to the **DataConnection** object, and commit the database changes. For more information, see [Transaction Support](../core/transaction-support.md).  

    ```  
    SqlConnection cn = new SqlConnection("Data Source=(local);Initial Catalog=TestDB;Integrated Security=SSPI");  
    cn.Open();  
    //Begin the transaction  
    SqlTransaction  tn = cn.BeginTransaction();  
    //Pass the transaction object to the DataConnection constructor  
    DataConnection dc = new DataConnection("TestDB", "PO", cn, tn);  
    Policy policy = new Policy("ProcessPurchaseOrderDbNet");  
    DebugTrackingInterceptor dti = new DebugTrackingInterceptor("c:\\Trace.txt");  
    policy.Execute(dc, dti);  
    dc.Update();  
    //Commit the database transaction  
    tn.Commit();  
    cn.Close();  
    ```  

## See Also  
 [Selecting Facts](../core/selecting-facts.md)