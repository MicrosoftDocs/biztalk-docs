---
description: "Learn more about: Passing Database Facts to the Business Rule Engine"
title: "Passing Database Facts to the Business Rule Engine"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Passing Database Facts to the Business Rule Engine
When you use the Business Rule Composer tool to test a policy that requires a DataConnection/TypedDataTable object as a fact, a DataConnection/TypedDataTable object is automatically created for you and asserted into the Business Rule Engine's working memory. Additionally, any database updates by the policy are committed automatically.  
  
 In contrast, when you invoke the policy from an orchestration, either by using the Call Rules shape or programmatically, the DataConnection/TypedDataTable object is not created for you and the database updates are not committed automatically. In this case, you should create a DataConnection/TypedDataTable object, pass it as a fact to the rule engine, and commit the database changes programmatically by using one of the following methods.  
  
## Passing a DataConnection Object from an Orchestration  

The following sample code demonstrates how to create a DataConnection object in the orchestration, configure the Call Rules shape to pass the DataConnection object as a parameter, and commit any database updates after the policy is executed.  

 
1.  Create the following variables using the Orchestration View tab with the orchestration open in the Orchestration Designer.  
  
    ```  
    DataCon of type Microsoft.RuleEngine.DataConnection   
    SqlCon of type System.Data.SqlClient.SqlConnection   
    SqlTran of type System.Data.SqlClient.SqlTransaction   
    ```  
  
2.  In an Expression shape before the Call Rules shape, create a DataConnection object. The following code example demonstrates how to create a DataConnection object.  
  
    ```  
    SqlCon.ConnectionString = "Data Source=(local);Initial Catalog=Test;Integrated Security=SSPI";   
    SqlCon.Open();   
    SqlTran = SqlCon.BeginTransaction();   
    DataCon = new Microsoft.RuleEngine.DataConnection("test", "FlagTable", SqlCon, SqlTran);    
    ```  

    [!INCLUDE [authentication-guidance](../includes/authentication-guidance.md)]

3.  Configure the Call Rules shape to pass the DataCon variable as a parameter. For more information, see [How to Use the Call Rules Shape](../core/how-to-use-the-call-rules-shape.md).  
  
4.  In an Expression shape after the Call Rules shape, commit the database changes made by the policy. The following code example demonstrates how to commit the database changes made by the policy.  
  
    ```  
    DataCon.Update();   
    SqlTran.Commit();  
    ```  
  
> [!NOTE]
>  You need to use a [SqlTransaction](/dotnet/api/system.data.sqlclient.sqltransaction) object only if the policy updates the database.  
  
## Passing a DataConnection Object from a Fact Retriever  
 Here are the typical steps you need to implement to pass a DataConnection object from a fact retriever component.  
  
1.  Create a fact retriever component that creates and asserts a DataConnection object into the rule engine's working memory. For more information about how to create a fact retriever component, see [How to Create a Fact Retriever](../core/how-to-create-a-fact-retriever.md).  
  
2.  Implement the [IFactRemover](/dotnet/api/microsoft.ruleengine.ifactremover) interface on fact retriever component, and commit the database changes from the [UpdateFactsAfterExecution](/dotnet/api/microsoft.ruleengine.ifactremover.updatefactsafterexecution) method. This method is called by the rule engine after it is done with executing the policy.  
  
3.  Configure the policy to use the fact retriever component by using the Business Rule Composer tool. For more information, see [How to Configure a Fact Retriever for a Policy](../core/how-to-configure-a-fact-retriever-for-a-policy.md).  
  
## See Also  
 [Data Access in the Business Rule Engine](../core/data-access-in-the-business-rule-engine.md)   
 [How to Create a Fact Retriever](../core/how-to-create-a-fact-retriever.md)   
 [How to Configure a Fact Retriever for a Policy](../core/how-to-configure-a-fact-retriever-for-a-policy.md)
