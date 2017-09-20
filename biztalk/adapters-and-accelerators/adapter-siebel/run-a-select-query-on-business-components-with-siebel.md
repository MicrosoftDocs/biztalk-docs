---
title: "Run a SELECT Query on Business Components with Siebel | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "performing operations, selecting data using ADO.NET provider"
  - "how to, select data in business components using ADO.NET provider"
ms.assetid: 34a22c2e-6fc9-4760-90a1-131a38ae947b
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Run a SELECT Query on Business Components with Siebel
This section demonstrates how to select data from a Siebel business component using the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)].  
  
## Selecting Data from a Siebel Business Component  
 This section demonstrates how to select data from the "Account" business component in the Siebel repository.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data.Common;  
using Microsoft.Adapters.SiebelDbProvider;  
  
namespace SiebelADO  
{  
 class Program  
  {  
   static void Main(string[] args)  
    {  
     try  
      {  
        SiebelProviderFactory factory = SiebelProviderFactory.Instance;  
        DbConnection connection = factory.CreateConnection();  
        connection.ConnectionString = "Username=SADMIN;Password=SADMIN;ServiceUri=172.23.115.223:2321;SiebelObjectManager=SSEObjMgr;SiebelEnterpriseServer=ent771;Language=enu;SiebelRepository=Siebel Repository";  
  
         connection.Open();  
         DbCommand command = connection.CreateCommand();  
  
         //Here is a list of sample commands. The second command shows how the Siebel ViewMode can be specified in the query.  
         //command.CommandText = "SELECT * from Account.Account where [Name] LIKE '3Com'";  
         //command.CommandText = "Select [Name] from [Account].[Account] where [Name] LIKE '3Com' OPTION ‘ViewMode 1’";  
           command.CommandText = "SELECT [Name], [Postal Code], Id From Account.Account where [Postal Code] != '60626' Order BY Id ASC, Name DESC";  
  
         DbDataReader dbReader = command.ExecuteReader();  
  
         while (dbReader.Read())  
           {  
              for (int i = 0; i < dbReader.FieldCount; i++)  
               {  
                 string name = dbReader.GetName(i);  
                 string val = dbReader[i].ToString();  
                 Console.WriteLine(name + "\t:" + val);  
                 Console.WriteLine("=========================");  
               }  
           }  
             Console.WriteLine("Press any key...");  
             Console.ReadLine();  
       }  
       catch (Exception exp) { Console.WriteLine(exp.Message); }  
       }  
    }  
}  
```  
  
## See Also  
 [Use the .NET Framework Data Provider for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)   
 [Run an EXECUTE Operation on Business Services with Siebel](../../adapters-and-accelerators/adapter-siebel/run-an-execute-operation-on-business-services-with-siebel.md)