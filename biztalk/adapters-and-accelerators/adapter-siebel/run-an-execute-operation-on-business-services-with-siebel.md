---
description: "Learn more about: Run an EXECUTE Operation on Business Services with Siebel"
title: "Run an EXECUTE Operation on Business Services with Siebel | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "how to, execute business services using ADO.NET Provider"
  - "performing operations, executing business services using ADO.NET Provider"
ms.assetid: c8f7888f-72c6-4f20-b592-f233721fbddd
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Run an EXECUTE Operation on Business Services with Siebel
This section demonstrates how to execute an operation on a Siebel business service using the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)].  
  
## Executing a Siebel Business Service  
 This section demonstrates how to execute operations on a business service in the Siebel repository.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data.Common;  
using System.Data;  
using Microsoft.Adapters.SiebelDbProvider;  
  
namespace SiebelADOBS  
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
        command.CommandText = "EXEC ExtractDataService.Echo @In, @InOut, @Out OUTPUT";  
  
        //Add @In  
        DbParameter param1 = command.CreateParameter();  
        param1.ParameterName = "@In";  
        param1.Direction = ParameterDirection.Input;  
        param1.Value = "SomethingElse";  
        command.Parameters.Add(param1);  
  
        //Add @InOut  
        DbParameter param2 = command.CreateParameter();  
        param2.ParameterName = "@InOut";  
        param2.Direction = ParameterDirection.InputOutput;  
        command.Parameters.Add(param2);  
  
        //Add @Out  
        DbParameter outParam = command.CreateParameter();  
        outParam.ParameterName = "@Out";  
        outParam.Direction = ParameterDirection.Output;  
        command.Parameters.Add(outParam);  
  
        DbDataReader dbReader = command.ExecuteReader();  
  
        Console.WriteLine("Param2: " + param2.Value);  
        Console.WriteLine("OutParam: " + outParam.Value);  
  
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
 [Run a SELECT Query on Business Components with Siebel](../../adapters-and-accelerators/adapter-siebel/run-a-select-query-on-business-components-with-siebel.md)
