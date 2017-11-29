---
title: "How to Populate a Host File Dataset from the Data Adapter2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 808e7265-ce85-41b9-9b3f-6a9441c1c489
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Populate a Host File Dataset from the Data Adapter
The dataset is a memory-resident representation of data that provides a consistent relational programming model independent of the data source. The dataset represents a complete set of data including tables, constraints, and relationships among the tables. Because the dataset is independent of the data source, a dataset can include data local to the application, and also data from multiple data sources. Interaction with existing data sources is controlled through the `DataAdapter` object.  
  
 The `HostfileDataAdapter.SelectCommand` property is a `HostFileCommand` object that retrieves data from the data source. The `HostFileDataAdapter.Fill` method is used to populate a dataset with the results of the `SelectCommand`. `Fill` takes as its arguments a `DataSet` object to be populated, and a `DataTable` object, or the name of the `DataTable` to be filled with the rows returned from the `SelectCommand`.  
  
 The `Fill` method uses the `HostFileDataReader` object implicitly to return the column names and types used to create the tables in the `DataSet` object, and also the data to populate the rows of the tables in the `DataSet` object. Tables and columns are only created if they do not already exist; otherwise `Fill` uses the existing `DataSet` schema. Primary keys are not created unless they are in the data source, and `HostFileDataAdapter.MissingSchemaAction` is set to `MissingSchemaAction.AddWithKey`. If `Fill` finds that a primary key exists for a table, it overwrites data in the `DataSet` object with data from the data source for rows where the primary key column values match those of the row returned from the data source. If no primary key is found, the data is appended to the tables in the `DataSet` object. `Fill` uses any mappings that might exist when populating the `DataSet` object.  
  
 If the `HostFileDataAdapter` encounters multiple result sets, it creates multiple tables in the `DataSet` object. The tables are given an incremental default name of TableN, starting with "Table" for Table0. If a table name is passed as an argument to the `Fill` method, the tables are given an incremental default name of TableNameN, starting with "TableName" for TableName0.  
  
 You can use any number of `HostFileDataAdapter` objects with a `DataSet` object. Each `DataAdapter` object can be used to fill one or more `DataTable` objects and resolve updates back to the relevant data source. You can add `DataRelation` and `Constraint` objects to the `DataSet` locally, enabling you to relate data from dissimilar data sources. One or more `DataAdapter` objects can handle communication to each data source.  
  
### To populate a host file dataset from the data adapter  
  
1.  Create a new connection to your data source by using `HostFileConnection`.  
  
2.  Open the connection by using `HostFileConnection.Open`.  
  
3.  Create a SELECT command that describes the data to retrieve with `HostFileCommand`.  
  
4.  Create a `HostFileDataAdapter` using `HostFileConnection` to interact with the stored data.  
  
5.  Create a `DataSet` object to store the data locally.  
  
6.  Retrieve the data through the `HostFileDataAdapter` using the `DataSet` object and the `Fill` command.  
  
## Example  
 The following code example shows how to fill a dataset through a `HostFileDataAdapter`. In this example, the ETCMLogging and HostFileUtils objects supply logging and utility functionality, respectively.  
  
```  
public void HFDAdapterCommandConstructor(ETCMLogging.Logging logging, string host, string ccsid, string cnstring, HostFileUtils.Utils.HostFileType hostfiletype)  
        {  
            HostFileUtils.Utils u = new HostFileUtils.Utils();  
            logging.LogInfo(host + "::" + hostfiletype.ToString());  
            HostFileUtils.Utils.MytestsVals[] Datavals = u.InitMytestsVals();  
  
            try  
            {  
                HostFileConnection cn = new HostFileConnection(cnstring);  
                cn.Open();  
                String SELECT = u.CreateSQLCommand(host, hostfiletype, cnstring, "SELECT", "MYTEST");  
                HostFileCommand hfc = new HostFileCommand(SELECT, cn);  
                HostFileDataAdapter hfda = new HostFileDataAdapter(hfc);  
                DataSet ds = new DataSet();  
                hfda.Fill(ds);  
                int[] cp = u.CheckColumns(SELECT, cn, logging);  
                u.ValidateDataSet(ds, logging, Datavals, cp);  
  
                cn.Close();  
            }  
            catch (Exception e)  
            {  
                logging.LogInfo(e.Message);  
                logging.LogFail(e.StackTrace);  
            }  
        }  
```  
  
 In this code example, the `HostFileUtils` object and the `cnstring` and `ccsid` parameters enable you to quickly create a test SQL command with the relevant information.  
  
## See Also  
 [Working with the Host File Adapter and Dataset](../core/working-with-the-host-file-adapter-and-dataset.md)   
 [BizTalk Adapter for Host Files Configuration](../Topic/BizTalk%20Adapter%20for%20Host%20Files%20Configuration2.md)