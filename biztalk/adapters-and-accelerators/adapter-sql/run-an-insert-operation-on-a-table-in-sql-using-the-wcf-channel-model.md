---
description: "Learn more about: Run an Insert Operation on a Table in SQL using the WCF Channel Model"
title: "Run an Insert Operation on a Table in SQL using the WCF Channel Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3df95d78-3a9c-48c0-81ab-1f3206c5e3f7
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Run an Insert Operation on a Table in SQL using the WCF Channel Model
The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] discovers a set of basic Insert, Select, Update, and Delete operations on SQL Server database tables and views. By using these operations, you can perform simple SQL Insert, Select, Update, and Delete statements qualified by a Where clause on a target table or view. This topic provides instructions on how to perform an Insert operation on a SQL Server database table using the WCF channel model.  
  
 For more information on how the adapter supports these operations, see [Insert, Update, Delete, and Select Operations on Tables and Views with the SQL adapter](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md). For more information about how to perform operations on SQL Server using the WCF Channel model, see [Overview of the WCF channel model with the SQL adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md).  
  
## About the Examples Used in this Topic  
 The example in this topic performs operations on the Employee table. The Employee table is created by running the SQL script provided with the samples. For more information about samples, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md). A sample, **EmployeeInsertOp**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.  
  
## The Insert Message  
 To perform operations on the SQL Server database using the WCF channel model, you must have the request message specific to the operation. The request message to perform an Insert operation on the Employee table in the SQL Server database resembles the following:  
  
```  
<Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
  <Rows>  
    <Employee xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
      <Name>Tom Smith</Name>  
      <Designation>Manager</Designation>  
      <Salary>500000</Salary>  
   </Employee>  
  </Rows>  
</Insert>  
```  
  
 This request message inserts a record with following details:  
  
```  
Name = Tom Smith  
Designation = Manager  
Salary = 500000  
```  
  
 You must copy the message to a file, e.g. InsertRequest.xml. This file is used in this example to send the request message to SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. For more information about the message schema for operations on table, see [Message Schemas for Insert, Update, Delete, and Select Operations on Tables and Views](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).  
  
## Creating a WCF Channel Application  
 This section provides instructions on how to create a WCF channel application to perform an Insert operation on the Employee table.  
  
#### To create a WCF channel application for inserting records into the Employee table  
  
1.  Create a Visual C# project in Visual Studio. For this topic, create a console application.  
  
2.  In the Solution Explorer, add reference to `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, and `System.Runtime.Serialization`.  
  
3.  Open the Program.cs file and add the following namespaces:  
  
    -   `Microsoft.Adapters.Sql`  
  
    -   `Microsoft.ServiceModel.Channels`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  Create the binding and endpoint.  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    EndpointAddress address = new EndpointAddress("mssql://mysqlserver//mydatabase?");  
  
    ```  
  
5.  Create and open the channel factory. This application sends request message to SQL Server and receives a response, hence you must implement the IRequestChannel interface.  
  
    ```  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    factory.Credentials.UserName.UserName = "<Enter user name here>";  
    factory.Credentials.UserName.Password = "<Enter password here>";  
    factory.Open();  
    ```  
  
6.  Create and open the channel.  
  
    ```  
    IRequestChannel channel = factory.CreateChannel();  
    channel.Open();  
    ```  
  
7.  Create and send the request message.  
  
    ```  
    XmlReader readerIn;  
    Console.WriteLine("Creating the message");  
    try  
    {  
       readerIn = XmlReader.Create("InsertRequest.xml");  
       Console.WriteLine("Reader created");  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    Message messageIn = Message.CreateMessage(MessageVersion.Default, "TableOp/Insert/dbo/Employee", readerIn);  
    Message messageOut = channel.Request(messageIn);  
  
    ```  
  
     While creating the request message, you must specify the message action that indicates the action that the adapter performs on the SQL Server table. To perform an Insert operation on the Employee table, the message action is `TableOp/Insert/dbo/Employee`. For information about how you can determine the message action for various operations on tables, see [Message Schemas for Insert, Update, Delete, and Select Operations on Tables and Views](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).  
  
8.  Get the response message.  
  
    ```  
    XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
    XmlDocument doc = new XmlDocument();  
    doc.Load(readerOut);  
    doc.Save("C:\\Response.xml");  
    ```  
  
9. Close the message, channel, and channel factory.  
  
    ```  
    messageOut.Close();  
    channel.Close();  
    factory.Close();  
    ```  
  
10. Build the project. After building the project, you must perform the following tasks:  
  
    -   Copy the request message, InsertRequest.xml, at the same location as your project executable. Typically, this location is \bin\Debug\ under your project directory.  
  
    -   The "Employee" table used in this example has a column of Point user-defined type (UDT). So, before running the project, you must create the assembly for the Point UDT as described at [Creating User-Defined Types](/sql/relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types). You must also copy the assembly DLL at the same location as the project executable. Typically, this location is \bin\Debug\ under your project directory.  
  
11. Run the application. The response message, Response.xml, is saved at the location you specified in the application. The response message contains the ID of the newly added employee and resembles the following:  
  
    ```  
    <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
      <InsertResult>  
        <long xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">10006</long>  
      </InsertResult>  
    </InsertResponse>  
    ```  
  
     Because the Employee table has the Employee_ID column as the identity column, the Insert operation returns the value for the identity column of the newly inserted record. If there is no identity column in a table, the return value is NULL.  
  
## See Also  
[Develop SQL applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)