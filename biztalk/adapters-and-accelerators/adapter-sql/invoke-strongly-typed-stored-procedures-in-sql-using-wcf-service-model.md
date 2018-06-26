---
title: "Invoke Strongly-typed Stored Procedures in SQL using WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d56df5f6-b046-4fe4-a5b4-b29906093beb
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invoke Strongly-typed Stored Procedures in SQL using WCF Service Model
When you invoke a procedure listed under the **Strongly-Typed Procedures** node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], the output is in the form of a strongly-typed result set. This topic provides instructions on how to create a WCF client to invoke stored procedures in SQL Server that return a strongly-typed result set.  
  
> [!NOTE]
>  If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on Tables and Views with User-Defined Types](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) before you start developing your application.  
  
## About the Examples Used in this Topic  
 The example in this topic uses the GET_EMP_DETAILS stored procedure. This stored procedure takes an employee ID as an input parameter and returns all the corresponding columns for the employee with that ID. The GET_EMP_DETAILS stored procedure is created by running the SQL script provided with the samples. For more information about samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md). A sample, **Execute_TypedStoredProcedure**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.  
  
## The WCF Client Class  
 The name of the WCF client generated for invoking stored procedures under the **Strongly-Typed Procedures** node using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is listed in the following table.  
  
|SQL Server Database Artifact|WCF Client Name|  
|----------------------------------|---------------------|  
|Procedure (under the **Strongly-Typed Procedures** node)|TypedProcedures_[schema]Client|  
  
 [schema] is the schema to which the procedure belongs; for example “dbo”.  
  
### Method Signature for Invoking Stored Procedures  
 The following table shows the signature for the method exposed to invoke the stored procedures.  
  
|Operation|Method Signature|  
|---------------|----------------------|  
|Procedure name|[PROC_NS] [procedure_name](param1, param2, …\)|  
  
 [PROC_NS] is the procedure namespace; for example schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[]  
  
 [procedure_name] is the name of the procedure; for example GET_EMP_DETAILS  
  
 As an example, the signature for the method to invoke the GET_EMP_DETAILS procedure is shown in the following code snippet.  
  
```  
public partial class TypedProcedures_dboClient : System.ServiceModel.ClientBase<TypedProcedures_dbo>, TypedProcedures_dbo{  
public schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[]   
  GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue);  
}  
```  
  
 In this snippet,  
  
-   `TypedProcedures_dboClient` is the name of the class. In this example, you use this class to create a client to invoke the stored procedure.  
  
-   `public schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue)` is the method that you invoke in this example to invoke the stored procedure. This stored procedure takes an employee ID and returns a strongly-typed result set.  
  
## Creating a WCF Client to Invoke a Stored Procedure in SQL Server  
 The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the SQL Adapter](overview-of-the-wcf-service-model-with-the-sql-adapter.md). This section specifically describes how to create a WCF client that invokes a stored procedure, the result set for which is strongly-typed. In this topic, as an example, you invoke the GET_EMP_DETAILS stored procedure. This stored procedure is created by running the SQL script provided with each sample.  
  
1. Create a Visual C# project in Visual Studio. For this topic, create a console application.  
  
2. Generate the WCF client class for the GET_EMP_DETAILS stored procedure. Make sure you select the procedure under the **Strongly-Typed Procedures** node. For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
   > [!IMPORTANT]
   >  Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.  
  
3. In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.  
  
4. Open the Program.cs file and create a client as described in the snippet below.  
  
   ```  
  
             TypedProcedures_dboClient client = new TypedProcedures_dboClient("SqlAdapterBinding_TypedProcedures_dbo");  
   client.ClientCredentials.UserName.UserName = "<Enter username here>";  
   client.ClientCredentials.UserName.Password = "<Enter username here>";  
   ```  
  
    In this snippet, `TypedProcedures_dboClient` is the WCF client defined in SqlAdapterBindingClient.cs. This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. `SqlAdapterBinding_TypedProcedures_dbo` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.  
  
   > [!NOTE]
   >  In this snippet, you use the binding and endpoint address from the configuration file. You can also explicitly specify these values in your code. For more information on the different ways of specifying client binding, see [Configure a Client Binding for the SQL Adapter](configure-a-client-binding-for-the-sql-adapter.md).  
  
5. Open the client as described in the snippet below:  
  
   ```  
   try  
   {  
      Console.WriteLine("Opening Client...");  
      client.Open();  
   }  
   catch (Exception ex)  
   {  
      Console.WriteLine("Exception: " + ex.Message);  
      throw;  
   }  
   ```  
  
6. Invoke the GET_EMP_DETAILS stored procedure as described in the snippet below.  
  
   ```  
   // Create array of type as specified in the method signature  
   schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[] resultSet =  
      new schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[1];  
   int returnCode;  
  
   try  
   {  
      Console.WriteLine("Calling a stored procedure...");  
      resultSet = client.GET_EMP_DETAILS(10001, out returnCode);  //Invoke the stored procedure  
   }  
   catch (Exception ex)  
   {  
      Console.WriteLine("Exception: " + ex.Message);  
      throw;  
   }  
   Console.WriteLine("The details for the employee with ID '10001' are:");  
   Console.WriteLine("*************************************************");  
  
   for (int i = 0; i < resultSet.Length; i++)  
      {  
         Console.WriteLine("Employee Name        : " + resultSet[i].Name);  
         Console.WriteLine("Employee Designation : " + resultSet[i].Designation);  
         Console.WriteLine("Employee Salary      : " + resultSet[i].Salary);  
      }  
  
   Console.WriteLine("*************************************************");  
  
   ```  
  
7. Close the client as described in the snippet below:  
  
   ```  
   client.Close();  
   Console.WriteLine("Press any key to exit...");  
   Console.ReadLine();  
   ```  
  
8. Build the project and then run it. The name, designation, and salary for the employee ID, are displayed on the console.  
  
## See Also  
[Develop applications using the WCF Service model](develop-sql-applications-using-the-wcf-service-model.md)