---
title: "Transaction Support | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DataConnection object"
  - "Business Rules Framework, code samples"
  - "Business Rules Framework, programming"
ms.assetid: 84faac2f-6229-4692-9d1a-bf62d87d69bb
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Transaction Support
The rule engine does not support transactions in general. However, you can update a database in a transactional manner by using the **DataConnection** object as shown in the following steps:  
  
1. Create a **SqlConnection** object by using a connection string, and open the connection.  
  
   ```  
   SqlConnection connection = new SqlConnection("Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;");  
   connection.Open();  
   ```  
  
2. Create a **SqlTransaction** object by calling the **BeginTransaction** method on the connection object you created in step 1.  
  
   ```  
   SqlTransaction transaction = connection.BeginTransaction();  
   ```  
  
3. Create a **DataConnection** object by using the connection and transaction objects you created in steps 1 and 2.  
  
   ```  
   DataConnection dc = new DataConnection(datasetName, tableName, connection, transaction);  
   ```  
  
4. Pass the **DataConnection** object as a fact along with any other facts you want to pass to the policy, and execute the policy.  
  
   ```  
   //Passing a .NET object as a fact along with the data connection  
   MyClass obj = new MyClass();  
   object[] facts = new object[2];  
   facts[0] = dc;  
   facts[1] = obj;  
   Policy pol = new Policy(policyName);  
   policy.Execute(facts);    
   ```  
  
5. Invoke the **Update** method on the data connection object. All the updates done while executing the policy are done only in memory. You must call the **Update** method on the data connection object to update the database.  
  
   ```  
   dc.Update();  
   ```  
  
6. Now, invoke **Commit** or **Rollback** on the data connection object based on your own logic.  
  
   ```  
   //Checking the value of PropertyA in .net object   
   //to decide whether to commit or rollback  
   if (obj.PropertyA == true)  
   transaction.Commit();  
   else  
   transaction.Rollback();  
  
   ```  
  
7. Close the connection, and dispose the policy object.  
  
   ```  
   sqlCon.Close();  
   policy.Dispose();  
   ```  
  
   The following code is the complete code with all the steps:  
  
```  
SqlConnection connection = new SqlConnection("Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;");  
connection.Open();  
SqlTransaction transaction = connection.BeginTransaction();  
DataConnection dc = new DataConnection(datasetName, tableName, connection, transaction);  
MyClass obj = new MyClass();  
object[] facts = new object[2];  
facts[0] = dc;  
facts[1] = obj;  
Policy pol = new Policy(policyName);  
policy.Execute(facts);    
dc.Update();  
if (obj.PropertyA == true)  
transaction.Commit();  
else  
transaction.Rollback();  
sqlCon.Close();  
policy.Dispose();  
```  
  
## Comments  
  
-   You can also use the **OleDbConnection** and **OleDbTransaction** objects instead of using the **SqlConnection** and **SqlTransaction** objects to perform database updates in a transactional manner.  
  
-   All the modifications done from the policy are done in memory. You must invoke the **Update** method on the **DataConnection** object to update the database.  
  
-   You can either commit or roll back the transaction by invoking the **Commit** or **Rollback** method of the **DataConnection** objects respectively.