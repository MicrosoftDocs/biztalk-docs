---
title: "ExecuteReader, ExecuteScalar, or ExecuteNonQuery operations in SQL using WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62f166af-b657-491b-b20d-1ae7886f27ce
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ExecuteReader, ExecuteScalar, or ExecuteNonQuery operations in SQL using WCF Service Model
The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes generic SQL Server operations such as **ExecuteNonQuery**, **ExecuteReader**, and **ExecuteScalar**. You can use these operations to execute any SQL statement on a SQL Server database. These operations differ based on the kind of response you get for the SQL statement. For more information about how the adapter supports these operations, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).  

 This topic demonstrates how to perform an **ExecuteReader** operation using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] using the WCF service model. You can follow the same set of procedures described in this topic to perform **ExecuteNonQuery** and **ExecuteScalar** operations.  

## About the Examples Used in this Topic  
 The example in this topic uses the **ExecuteReader** operation to execute the ADD_EMP_DETAILS stored procedure. This stored procedure adds a record to the Employee table and returns the employee ID for the record. The ADD_EMP_DETAILS stored procedure is created by running the SQL script provided with the samples. For more information about samples, see [Adapter samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md). A sample, **Execute_Reader**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.  

## The WCF Client Class  
 The name of the WCF client generated for invoking generic operations (ExecuteNonQuery, ExecuteReader, or ExecuteScalar) using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is listed in the following table.  

|Operations|WCF Client Name|  
|----------------|---------------------|  
|ExecuteNonQuery, ExecuteReader, or ExecuteScalar|GenericTableOpClient|  

### Method Signature for Invoking Generic Operations  
 The following table shows the signature for the method exposed to invoke the generic operations.  

|Operation|Method Signature|  
|---------------|----------------------|  
|ExecuteNonQuery|int ExecuteNonQuery(string Query)|  
|ExecuteReader|System.Data.DataSet[] ExecuteReader(string Query)|  
|ExecuteScalar|string ExecuteScalar(string Query)|  

 As an example, the signature for the generic operation methods is shown in the following code snippet.  

```  
public partial class GenericTableOpClient : System.ServiceModel.ClientBase<GenericTableOp>, GenericTableOp {  
  public int ExecuteNonQuery(string Query);  
  public System.Data.DataSet[] ExecuteReader(string Query);  
  public string ExecuteScalar(string Query);  
}  
```  

 In this snippet,  

-   `GenericTableOpClient` is the name of the class. In this example, you use this class to create a client to invoke the generic operation, ExecuteReader.  

-   `public System.Data.DataSet[] ExecuteReader(string Query)` is the method that you invoke in this example to invoke the ADD_EMP_DETAILS stored procedure.  

## Creating a WCF Client to Invoke an ExecuteReader Operation  
 The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF channel model with the SQL adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md). This section specifically describes how to create a WCF client that invokes an **ExecuteReader** operation to execute the ADD_EMP_DETAILS stored procedure. This stored procedure is created by running the SQL script provided with each sample.  

#### To create a WCF client to invoke ExecuteReader operation  

1. Create a Visual C# project in Visual Studio. For this topic, create a console application.  

2. Generate the WCF client class for the **ExecuteReader** generic operation. This operation is available under the root node when you connect to the SQL Server database using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  

   > [!IMPORTANT]
   >  Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.  

3. In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.  

4. Open the Program.cs file and create a client as described in the snippet below.  

   ```  

           GenericTableOpClient client = new GenericTableOpClient("SqlAdapterBinding_GenericTableOp");  
   client.ClientCredentials.UserName.UserName = "<Enter username here>";  
   client.ClientCredentials.UserName.Password = "<Enter password here>";  
   ```  

    In this snippet, `GenericTableOpClient` is the WCF client defined in SqlAdapterBindingClient.cs. This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. `SqlAdapterBinding_GenericTableOp` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.  

   > [!NOTE]
   >  In this snippet, you use the binding and endpoint address from the configuration file. You can also explicitly specify these values in your code. For more information on the different ways of specifying client binding, see [Configure a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).  

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

6. Invoke the **ExecuteReader** operation for the ADD_EMP_DETAILS stored procedure. Before you invoke the ExecuteReader operation, you must add the `System.Data` namespace to your code.  

   ```  
   string query = "EXEC ADD_EMP_DETAILS 'Tom Smith', 'Manager', 500000";  
   DataSet[] dsArray = client.ExecuteReader(query);  

   Console.WriteLine("Invoking the ADD_EMP_DETAILS stored procedure using ExecuteReader");  
   Console.WriteLine("*****************************************************");  
   foreach (DataSet dataSet in dsArray)  
   {  
      foreach (DataTable tab in dsArray[0].Tables)  
      {  
          foreach (DataRow row in tab.Rows)  
          {  
             for (int i = 0; i < tab.Columns.Count; i++)  
             {  
                Console.WriteLine("The ID for the newly added employee is : " + row[i]);  
             }  
          }  
       }  
   }  
   Console.WriteLine("*****************************************************");  

   ```  

7. Close the client as described in the snippet below:  

   ```  
   client.Close();  
   Console.WriteLine("Press any key to exit...");  
   Console.ReadLine();  
   ```  

8. Build the project and then run it. The employee ID of the newly inserted employee is displayed on the console.
