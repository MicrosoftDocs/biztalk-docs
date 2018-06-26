---
title: "Invoke RFCs and BAPIs using the EXEC Command in SAP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "EXEC command, invoking RFCs and BAPIs"
  - "BAPIs and RFCs, invoking by using the EXEC command"
  - "RFCs and BAPIs, invoking by using the EXEC command"
ms.assetid: 55443679-2fa8-4c13-ac3b-1c85b5166cd2
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invoke RFCs and BAPIs using the EXEC Command in SAP
The [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] exposes the SAP system as an ADO.NET data source. By using [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], you can invoke RFCs and BAPIs on the SAP system through an EXEC command.  
  
## How to Invoke RFCs and BAPIs on the SAP system  
 To invoke an RFC or BAPI using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], perform the following steps:  
  
#### To invoke an RFC or BAPI  
  
1. Include a reference (and a using statement in your code) to **Microsoft.Data.SAPClient**.  
  
2. Create a **SAPConnection** object by using a Data Provider for SAP connection string. For more information about the connection string, see [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).  
  
3. Open a connection to the SAP system by invoking **Open** on the **SAPConnection**.  
  
4. Create a **SAPCommand** object from the **SAPConnection**.  
  
5. Specify the BAPI or RFC call in the **CommandText** property of the **SAPCommand**. If necessary, you can specify parameters using **SAPParameter** objects. For more information about how to specify a BAPI or RFC call using an EXEC statement, see [Syntax for an EXEC Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-exec-statement-in-sap.md). For examples of how to specify a BAPI or RFC, see [Examples for EXEC Statement](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md).  
  
6. Execute the command to invoke the RFC or BAPI and obtain the results in a **SAPDataReader**.  
  
7. Read the results from the **SAPDataReader**.  
  
8. When you are finished using them, close (or dispose) the **SAPConnection** and the **SAPDataReader**.  
  
   The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] also exposes a **SAPClientFactory** class, which you can use to create **SAPConnection**, **SAPCommand** and **SAPConnection** objects. For more information about the ADO.NET classes extended by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Extend ADO.NET Interfaces with the SAP adapter](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md).  
  
## Example  
 The following example invokes SD_RFC_CUSTOMER_GET to retrieve customer information for all customers whose names start with "AB". It then writes the customer records to the console.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using Microsoft.Data.SAPClient;  
  
namespace SapAdoExec  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string connstr = "TYPE=A; ASHOST=YourSAPHost; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;";  
  
            using (SAPConnection conn = new SAPConnection(connstr))  
            {  
                conn.Open();  
  
                using (SAPCommand cmd = conn.CreateCommand())  
                {  
                    cmd.CommandText = "exec sd_rfc_customer_get @name1='AB*' ";  
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
                                    b.Append(dr[i].ToString() + " ");  
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
 [Samples](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)