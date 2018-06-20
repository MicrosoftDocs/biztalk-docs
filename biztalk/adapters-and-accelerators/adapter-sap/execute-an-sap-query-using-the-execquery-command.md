---
title: "Execute an SAP Query Using the EXECQUERY Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 520153bf-9477-4b35-8953-3f5cb444ab9f
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Execute an SAP Query Using the EXECQUERY Command
The [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] exposes the SAP system as an ADO.NET data source. With the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], you can execute pre-defined queries in the SAP system by executing an EXECQUERY statement.  
  
## How to Perform a Query by Using the EXECQUERY Command  
 To execute pre-defined SAP queries using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], perform the following steps:  
  
#### To perform a query  
  
1. Include a reference (and a using statement in your code) to **Microsoft.Data.SAPClient**.  
  
2. Create a **SAPConnection** object by using a Data Provider for SAP connection string. For more information about the connection string, see [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).  
  
3. Open a connection to the SAP system by invoking **Open** on the **SAPConnection**.  
  
4. Create a **SAPCommand** object from the **SAPConnection**.  
  
5. Specify the EXECQUERY statement in the **CommandText** property of the **SAPCommand**. If necessary, you can specify parameters using **SAPParameter** objects. For more information about how to execute queries defined in an SAP system using an EXECQUERY statement, see [Syntax for an EXECQUERY Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-execquery-statement-in-sap.md).  
  
6. Execute the command to perform the query and obtain the results in a **SAPDataReader**.  
  
7. Read the results from the **SAPDataReader**.  
  
8. When you are finished using them, close (or dispose) the **SAPConnection** and the **SAPDataReader**.  
  
   The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] also exposes a **SAPClientFactory** class, which you can use to create **SAPConnection**, **SAPCommand** and **SAPConnection** objects. For more information about the ADO.NET classes extended by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Extend ADO.NET Interfaces with the SAP adapter](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md).  
  
## Example  
 The following example writes the results of a query, ZTEST1, to the console.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using Microsoft.Data.SAPClient;  
  
namespace SapAdoExecQuery  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
           string connstr = "TYPE=A; ASHOST=YourSapHost; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;";  
           using (SAPConnection conn = new SAPConnection(connstr))  
            {  
                conn.Open();  
                using (SAPCommand cmd = conn.CreateCommand())  
                {  
                    cmd.CommandText = "EXECQUERY ZTEST1 @userGRoup='SYSTQV000024',@P1='0000001390',@P2='0000080150'";  
                    cmd.Parameters.Add(new SAPParameter("@connid", 17));                      
                    using (SAPDataReader dr = cmd.ExecuteReader())  
                    {  
                        do  
                        {  
                            int rows = 0;  
                            while (dr.Read())  
                            {  
                                rows++;  
                                StringBuilder b = new StringBuilder();  
                                for (int i = 0; i < dr.FieldCount; i++)  
                                {  
                                    b.Append(dr[i].ToString()+" ");  
                                }  
                                Console.WriteLine("row {0}: {1} ", rows, b.ToString());  
                            }  
                            Console.WriteLine("Number of rows:{0}", rows);  
                        } while (dr.NextResult());  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## See Also  
 [Use the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)  
 [Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)