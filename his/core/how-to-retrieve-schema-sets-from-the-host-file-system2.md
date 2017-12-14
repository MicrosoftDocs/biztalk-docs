---
title: "How to Retrieve Schema Sets from the Host File System2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27b4f55f-8a87-47f8-bc3a-f5642f4f997c
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Retrieve Schema Sets from the Host File System
When a `HostFileConnection` is open, you can retrieve schema information about the target data by using the `GetSchema` method. `GetSchema` returns a `DataTable` object populated with the rows and columns that contain the schema information of the target of the current connection.  
  
 In addition, while a `DBDataReader` is open, you can retrieve schema information about the current result set by using the `GetSchemaTable` method. `GetSchemaTable` returns a `DataTable` object populated with rows and columns that contain the schema information for the current result set. The `DataTable` object contains one row for each column of the result set. Each column of the schema table row maps to a property of the column returned in the result set, where the `ColumnName` is the name of the property and the value of the column is the value of the property.  
  
### To retrieve schema sets from the host file system  
  
1.  Open a connection to the host file system with a call to `HostFileConnection`.  
  
2.  Call `HostfileConnection.GetSchema` to retrieve the schema data.  
  
## Example  
 The following code example demonstrates how to retrieve the schema sets from a connection object. Note that the ETCMLogging and HostFileUtils objects are developer-created objects that provide logging and utility functionality.  
  
```  
public void CNGetSchema(ETCMLogging.Logging logging, string host, string ccsid, string cnstring, HostFileUtils.Utils.HostFileType hostfiletype)  
        {  
            HostFileUtils.Oledb oledb = new HostFileUtils.Oledb();  
            HostFileUtils.Utils u = new HostFileUtils.Utils();  
            logging.LogInfo(host);  
            try  
            {  
                // Create connection.  
                HostFileConnection cn = oledb.CreateConnection(logging);  
                cn.ConnectionString = cnstring;  
                DataTable dt = cn.GetSchema();  
                if (dt.HasErrors)  
                {  
                    logging.LogFail("returned datatable has errors");  
                }  
                // Open the connection.  
                logging.LogInfo("Open Connection");  
                cn.Open();  
                DataTable dt2 = cn.GetSchema();  
                if (dt2.HasErrors)  
                {  
                    logging.LogFail("returned datatable has errors");  
                }  
                int rowcnt = dt.Rows.Count;  
                for (int i = 0; i < rowcnt; i++)  
                {  
                    int colcnt = dt.Rows[i].ItemArray.Length;  
                    for (int o = 0; o < colcnt; o++)  
                    {  
                        u.CompareValues(dt.Rows[i][o].ToString(), dt2.Rows[i][o].ToString(), logging);                          
                    }  
                }  
                // Close the open connection.  
                cn.Close();  
            }  
            catch (Exception e)  
            {  
                logging.LogInfo(e.Message);  
                logging.LogFail(e.StackTrace);  
            }  
        }  
```  
  
## See Also  
 [Retrieving Information from the Host File System](../core/retrieving-information-from-the-host-file-system2.md)   
 [BizTalk Adapter for Host Files Configuration](./biztalk-adapter-for-host-files-configuration1.md)