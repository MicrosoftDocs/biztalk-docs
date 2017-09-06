---
title: "Complete operations on tables with large data types in Oracle Database using the WCF service model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF service model, performing operations on tables and views"
  - "how to, invoke the ReadLOB and UpdateLOB operations"
ms.assetid: 5d0e84d3-7ffa-47c7-aaf2-a1007f7a71a2
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Complete operations on tables with large data types in Oracle Database using the WCF service model
This section contains information about how to invoke the ReadLOB and UpdateLOB operations from the WCF service model. The ReadLOB and UpdateLOB operations are surfaced for tables and views that contain LOB columns; that is columns that are used to store Oracle large object (LOB) data. For an overview of the Oracle LOB data types supported by the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] and of the ReadLOB and UpdateLOB operations, see [Operations on Tables and Views That Contain LOB Data in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md).  
  
> [!IMPORTANT]
>  LOB data columns can contain large amounts of data—up to 4 gigabytes (GB). A significant limitation of using a WCF client to operate on LOB columns is that the WCF service model only supports data streaming on the ReadLOB operation, not on the UpdateLOB operation. This is because WCF requires that for streaming to work from service model, the parameter to be streamed must be the only parameter in its direction. The UpdateLOB operation has two other IN parameters (a column name and row filter) in addition to the LOB data; for this reason, streaming is not supported on it in the WCF service model. Therefore, if you are updating a LOB column with a large amount of data, you might want to use the WCF channel model. For more information on how to use the WCF channel model to stream LOB data using the UpdateLOB operation, see [Streaming Oracle LOB Data Types by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).  
  
## About the Examples Used in this Topic  
 The examples in this topic use the /SCOTT/CUSTOMER table. This table contains a BLOB column named PHOTO.A script to generate this table is supplied with the SDK samples. For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).  
  
## The WCF Client Class  
 The following example shows the method signatures for a WCF client class generated for the ReadLOB and UpdateLOB operations on the /SCOTT/CUSTOMER table.  
  
```  
public partial class SCOTTTableCUSTOMERClient : System.ServiceModel.ClientBase<SCOTTTableCUSTOMER>,   
                                                SCOTTTableCUSTOMER   
{  
    public System.IO.Stream ReadLOB(string LOB_COLUMN, string FILTER);   
  
    public void UpdateLOB(string LOB_COLUMN, string FILTER, byte[] Stream);  
}  
```  
  
> [!NOTE]
>  Note that **ReadLOB** returns a data stream, but that **UpdateLOB** does not operate on a stream.  
  
## Invoking the ReadLOB and UpdateLOB Operations  
 Both the **ReadLOB** and **UpdateLOB** methods can operate only on a single LOB column in a single database row. You set the following parameters to identify the target column/row.  
  
|Parameter|Definition|  
|---------------|----------------|  
|LOB_COLUMN|The name of the target column within the row identified by the FILTER parameter; for example, "PHOTO".|  
|FILTER|The contents of a SQL SELECT statement WHERE clause that specifies the target row; for example, "NAME='Kim Ralls'". The filter must specify one and only one row. If the filter matches more than one row:<br /><br /> -   **ReadLOB** returns LOB data for the first matching row.<br />-   **UpdateLOB** throws an exception.|  
  
> [!NOTE]
>  The stream returned by **ReadLOB** does not support **Seek**. This means that properties such as **Length** are not supported, either.  
  
> [!CAUTION]
>  The **UpdateLOB** operation must be performed within a transaction scope. Also, the **UseAmbientTransaction** binding property must be set to **true** before performing the **UpdateLOB** operation.  
  
 The following code shows how to use a WCF client to update the BLOB PHOTO column in the /SCOTT/CUSTOMER table from a file and read the new column data back to a file. You can find a full sample in the SDK samples. For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Transaction;  
  
// Include for file streaming  
using System.IO;  
  
// Add WCF, WCF LOB Adapter SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for the WCF channel model  
using System.ServiceModel.Channels;  
  
// Include this namespace for the WCF LOB Adapter SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
using CustomerTablens = microsoft.lobservices.oracledb._2007._03;  
  
namespace OracleLobOpsSnippetSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                OracleDBBinding binding = new OracleDBBinding();  
                binding.UseAmbientTransaction = true; //set this to true for UpdateLOB operation  
  
                EndpointAddress endpointAddress = new EndpointAddress("oracleDB://ADAPTER");  
  
                using (SCOTTTableCUSTOMERClient customerTableClient =  
                    new SCOTTTableCUSTOMERClient(binding, endpointAddress))  
                {  
                    customerTableClient.ClientCredentials.UserName.UserName = "SCOTT";  
                    customerTableClient.ClientCredentials.UserName.Password = "TIGER";  
  
                    // Open the client to read the LOB data back  
                    customerTableClient.Open();  
  
                    // Add a photo to the customer record    
                    using (FileStream fs = new FileStream("SamplePhoto.jpg", FileMode.Open))  
                    {  
                        Console.WriteLine("Updating photo");  
                        int count = 0;  
                        byte[] photo = new byte[fs.Length];  
                        while ((count += fs.Read(photo, count, (int) (((fs.Length-count)>4096)? 4096:fs.Length-count))) \< fs.Length) ;  
  
                        // UpdateLOB operation must be performed within a transaction scope  
                        using(TransactionScope tx = new TransactionScope())  
                        {  
                           customerTableClient.UpdateLOB("PHOTO", "NAME='Kim Ralls'", photo);  
                           Console.WriteLine("Photo updated");  
                           tx.Complete();  
                        }  
                    }  
  
                    // Read the data back and store it to another file  
                    using (FileStream fs = new FileStream("PhotoCopy.jpg", FileMode.Create))  
                    {  
                        Console.WriteLine("Reading photo data");  
                        Stream photoStream = customerTableClient.ReadLOB("PHOTO", "NAME='Kim Ralls'");  
                        Console.WriteLine("Photo data read -- writing to PhotoCopy.jpg");  
  
                        int count;  
                        int length = 0;  
                        byte[] buffer = new byte[4096];  
                        while ((count = photoStream.Read(buffer, 0, 4096)) > 0)  
                        {  
                            fs.Write(buffer, 0, count);  
                            length+=count;  
                        }  
                        Console.WriteLine("{0} bytes written to PhotoCopy.jpg", length);  
                    }  
  
                }  
  
                Console.WriteLine("Photo updated and read back -- Hit <RETURN> to end");  
                Console.ReadLine();  
  
            }  
            catch (Exception ex)  
            {  
                // handle exception  
                Console.WriteLine("Exception caught: " + ex.Message);  
            }  
        }  
    }  
}  
```  
  
## See Also  
 [Develop Oracle Database Applications Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)