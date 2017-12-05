---
title: "How to Perform a Two-Phase Commit Transaction over TCP-IP1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7439bb1-3106-44d1-9882-36eb34f9e595
caps.latest.revision: 3
---
# How to Perform a Two-Phase Commit Transaction over TCP/IP
Two-phase commit (2PC) is a host server-installed protocol that ensures that updates to multiple instances of a database on a network either succeed or fail in their entirety. [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] supports 2PC over TCP/IP, enabling you to gain the security of a 2PC connection over the Internet.  
  
 Host Integration Server supports 2PC works using three components: the Microsoft Distributed Transaction Coordinator (DTC), the Resync service, and the transaction log. The DTC governs the normal DTC transaction flow: enlist, prepare, commit, and abort. The Resync service coordinates transaction recovery in case of any failure or disconnection, while the transaction log maintains a log of information that is needed in case of recovery.  
  
 You can perform a 2PC transaction with ADO.NET and the Managed Provider for DB2 by using the `System.EnterpriseServices` namespace. Using a 2PC transaction is automatic. However, you may need to configure your 2PC connection by using tools such as the Data Access Tool.  
  
## Example  
 The following code example demonstrates how to use 2PC in a DB2 transaction.  
  
```  
Public class CentralBank : ServicedComponent  
{  
   public CentralBank()  
   {  
   }  
  
   public void Transfer(string connString, int fromId, int toId, double amount)  
   {  
      MsDb2Connection conn = null;  
      MsDb2Command cmd = null;  
      int rowsAffected = 0;  
      try  
      {  
         conn = new MsDb2Connection(connString);  
         conn.Open();  
  
         cmd = new MsDb2Command();  
         cmd.Connection = conn;  
         cmd.CommandText = "UPDATE ACCOUNTS SET BALANCE = BALANCE + ?   
WHERE ID = ?";  
         cmd.Parameters.Add("balance", amount);  
         cmd.Parameters.Add("toId", toId);  
         rowsAffected = cmd.ExecuteNonQuery();  
         cmd.Parameters.Clear();  
         cmd.CommandText = "UPDATE ACCOUNTS SET BALANCE = BALANCE - ?   
WHERE ID = ?";  
         cmd.Parameters.Add("balance", amount);  
         cmd.Parameters.Add("fromId", fromId);  
         rowsAffected = cmd.ExecuteNonQuery();  
         ContextUtil.SetComplete();  
      }  
      catch(MsDb2Exceptionsqlca)  
      {  
         Console.WriteLine(sqlca.Message);  
         ContextUtil.SetAbort();  
      }  
      finally  
      {  
         if(cmd != null)  
            cmd.Dispose();  
         if(conn != null)  
         {  
            if(conn.State == ConnectionState.Open)  
               conn.Close();  
            conn.Dispose();  
         }  
      }  
   }  
}  
```  
  
## See Also  
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db22.md)