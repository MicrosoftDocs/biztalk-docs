---
title: "How to Perform a Two-Phase Commit Transaction over TCP-IP2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2a63782-04b5-4e3a-a013-aa58955a89c5
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Perform a Two-Phase Commit Transaction over TCP/IP
Two-phase commit (2PC) is a host server-installed protocol that ensures that updates to multiple instances of a database on a network either succeed or fail in their entirety. [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] supports 2PC over TCP/IP, enabling you to gain the security of a 2PC connection over the Internet.  
  
 Host Integration Server supports 2PC works using two components: the Microsoft Distributed Transaction Coordinator (DTC), and the transaction log. The DTC governs the normal DTC transaction flow: enlist, prepare, commit, and abort. Also, DTC handles transaction recovery in case of any failure or disconnection, while the transaction log maintains a log of information that is needed in case of recovery.  
  
 You can perform a 2PC transaction with ADO.NET and the Managed Provider for DB2 by using the `System.Transactions` namespace. Using a 2PC transaction is automatic, when you configure the connection property Units of Work=DUW.  
  
## Example  
 The following code example demonstrates how to use 2PC in a DB2 transaction.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Data;  
using System.Transactions;  
using Microsoft.HostIntegration.MsDb2Client;  
  
namespace Db2DistributedTransaction  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Db2Tx();  
        }  
  
        static void Db2Tx()  
        {  
            string connectionStringDb2 = "Password=HISDEMO;User ID=HISDEMO;Initial Catalog=DSN1D037;Data Source=DSN8910;Network Transport Library=TCPIP;Host CCSID=37;PC Code Page=1208;Network Address=123.34.45.57;Network Port=446;Package Collection=HISDEMO;Default Schema=DSN8910;Default Qualifier=DSN8910;Units of Work=DUW;Defer Prepare=True;AutoCommit=False";  
            System.Transactions.CommittableTransaction transaction = new System.Transactions.CommittableTransaction();  
            MsDb2Connection connection = new MsDb2Connection(connectionStringDb2);  
            MsDb2Command command = new MsDb2Command();  
            try  
            {  
                connection.Open();  
                connection.EnlistTransaction(transaction);  
                command.Connection = connection;  
                command.CommandText = "INSERT INTO DSN8910.AREAS (AREAID, AREADESC, REGIONID) VALUES ('11111', 'Area 11111', 111)";  
                command.ExecuteNonQuery();  
                command.CommandText = "INSERT INTO DSN8910.AREAS (AREAID, AREADESC, REGIONID) VALUES ('22222', 'Area 22222', 222)";  
                command.ExecuteNonQuery();  
                while (true)  
                {  
                    Console.Write("Commit or Rollback? [C|R] ");  
                    ConsoleKeyInfo c = Console.ReadKey();  
                    Console.WriteLine();  
                    Console.ReadKey();  
  
                    if ((c.KeyChar == 'C') || (c.KeyChar == 'c'))  
                    {  
                        transaction.Commit();  
                        break;  
                    }  
                    else if ((c.KeyChar == 'R') || (c.KeyChar == 'r'))  
                    {  
                        transaction.Rollback();  
                        break;  
                    }  
                }  
                connection.Close();  
                transaction = null;  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Commit Exception Type: {0}", ex.GetType());  
                Console.WriteLine("  Message: {0}", ex.Message);  
                Console.ReadKey();  
            }  
            Console.WriteLine("Program end.");  
            Console.ReadKey();  
        }  
    }  
```  
  
## See Also  
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db21.md)