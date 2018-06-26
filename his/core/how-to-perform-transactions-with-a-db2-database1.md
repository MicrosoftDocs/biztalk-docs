---
title: "How to Perform Transactions with a DB2 Database1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20df9893-4238-4dce-b943-6e3d93543a92
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Perform Transactions with a DB2 Database
Transactions are a group of database operations combined into a logical unit of work, and are used to control and maintain the consistency and integrity of each database despite errors that might occur in the system. A transaction consists of a series of SQL SELECT, INSERT, UPDATE, or DELETE statements. If no errors occur during a transaction, all modifications in the transaction become a permanent part of the database. If errors occur, none of the modifications are made to the database.  
  
 A transaction is considered to be a local transaction when it is a single-phase transaction and is handled by the database directly. Transactions are considered to be distributed transactions when they are coordinated by a transaction monitor and use fail-safe mechanisms (such as two-phase commit) for transaction resolution.  
  
> [!NOTE]
>  Transactions are most efficient when they are performed on the server. If you are working with a SQL Server database that makes extensive use of explicit transactions, you should consider writing them as stored procedures using the Transact-SQL BEGIN TRANSACTION statement.  
  
 You control transactions with the `MsDb2Connection` object. You can initiate a local transaction with the `BeginTransaction` method. Once you have begun a transaction, you can enlist a command in that transaction with the `Transaction` property of an `MsDb2Command` object. You can then commit or roll back modifications made at the data source based on the success or failure of the components of the transaction.  
  
 There are three basic commands for transactions: BEGIN, COMMIT, and ROLLBACK. The BEGIN statement marks the beginning of a transaction. All procedures attempted after the BEGIN statement are considered part of the transaction, which is completed by the COMMIT statement, or canceled by the ROLLBACK statement.  
  
### To perform a transaction  
  
1. Call `MsDb2Connection.BeginTransaction` to mark the start of the transaction.  
  
    `BeginTransaction` returns a reference to the transaction. Retain this reference so that you can assign it to commands that are enlisted in the transaction.  
  
2. Assign the transaction to the `MsDb2Command.Transaction` to be executed.  
  
    If a command is executed on a connection with an active transaction and the `Transaction` object has not been assigned to the `Transaction` property of the `Command`, an `MsDb2Exception` is thrown.  
  
3. Execute the required commands.  
  
4. Call `MsDb2Transaction.Commit` to complete the transaction, or call `MsDb2Transaction.Rollback` to cancel the transaction.  
  
    If the connection is closed or disposed before either the `Commit` or `Rollback` methods have been executed, the transaction is rolled back.  
  
   The following code example demonstrates how to perform a transaction.  
  
```  
static void TransactionConnection()  
{  
    MsDb2Connection myConnection new MsDb2Connection(@"file name=HOST.udl ");  
    myConnection.Open();  
    // Start a local transaction.  
    MsDb2Transaction myTrans = myConnection.BeginTransaction();  
    // Enlist the command in the current transaction.  
    MsDb2Command myCommand = myConnection.CreateCommand();  
    myCommand.Transaction = myTrans;  
    try  
    {  
        myCommand.CommandText = "Insert into Region (RegionID, RegionDescription) VALUES (100, 'Description')";  
        myCommand.ExecuteNonQuery();  
        myCommand.CommandText = "Insert into Region (RegionID, RegionDescription) VALUES (101, 'Description')";  
        myCommand.ExecuteNonQuery();  
        myTrans.Commit();  
        Console.WriteLine("Both records are written to database.");  
    }  
    catch(Exception e)  
    {  
        try  
        {  
           myTrans.Rollback();  
        }  
        catch (MsDb2Exception ex)  
        {  
            if (myTrans.Connection != null)  
            {  
                Console.WriteLine("An exception of type " + ex.GetType() +  
                    " was encountered while attempting to roll back the transaction.");  
            }  
        }  
  
        Console.WriteLine("An exception of type " + e.GetType() +  
            "was encountered while inserting the data.");  
        Console.WriteLine("Neither record was written to database.");  
    }  
    finally  
    {  
        Console.ReadLine();  
        myConnection.Close();  
    }  
}   
// End TransactionConnection  
  
```  
  
## See Also  
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db21.md)