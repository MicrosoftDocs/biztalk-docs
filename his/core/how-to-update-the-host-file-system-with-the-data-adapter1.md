---
title: "How to Update the Host File System with the Data Adapter1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec0bd859-9d0c-4f60-91fe-ee8949997f3f
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Update the Host File System with the Data Adapter
`HostFileDataAdapter.Update` is called to resolve changes from a `DataSet` object back to the data source. The `Update` method, like the `Fill` method, takes an instance of a `DataSet` as an argument.  
  
### To update the host file system with the data adapter  
  
1.  Create a `DataSet` object that contains the information that you want to update.  
  
     Or, you can overwrite the data of an existing `DataSet` object with a call to `DataSet.AcceptChanges`.  
  
     Note that calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` object causes all Original values for a `DataRow` object to be overwritten with the Current values for the `DataRow`. If the field values that identify the row as unique have been modified, after you call `AcceptChanges`, the Original values no longer match the values in the data source.  
  
     In addition, you can use `HostFileCommand` parameters to specify input and output values for a SQL statement for each modified row in a `DataSet` object.  
  
2.  Call `HostFileDataAdapter.Update`, with the DataSet object that you want to update.  
  
     When you call the `Update` method, the `HostFileDataAdapter` analyzes the changes that have been made and executes the appropriate command. If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.  
  
3.  If you want to update your dataset with data, call `HostFileDataAdapter.Fill` on your `DataSet` object.  
  
     The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the DataSet. New rows are added to the table, and updated information is incorporated into existing rows.  
  
## Example  
 The following code example demonstrates how to updating a dataset with the `Fill` and `Update` commands. Note that the ETCMLogging and HostFileUtils objects provide logging and utility functionality, respectively.  
  
```  
public void BVTHFDataAdapterInsert(ETCMLogging.Logging logging, string host, string ccsid, string cnstring, HostFileUtils.Utils.HostFileType hostfiletype)  
        {  
            HostFileUtils.Utils u = new HostFileUtils.Utils();  
            logging.LogInfo(host + "::" + hostfiletype.ToString());  
            HostFileUtils.Utils.BvttestsVals[] Datavals = u.InitBvttestsVals();  
  
            try  
            {  
                HostFileConnection cn = new HostFileConnection(cnstring);  
                cn.Open();  
                String SELECT = u.CreateSQLCommand(host, hostfiletype, cnstring, "SELECT", "BVTTESTS");  
                HostFileDataAdapter hfda = new HostFileDataAdapter(SELECT, cn);  
                DataSet ds = new DataSet();                DataSet dsold = new DataSet();                hfda.Fill(ds);                hfda.Fill(dsold);  
                int[] cp = u.CheckColumns(SELECT, cn, logging);  
                u.ValidateDataSet(ds, logging, Datavals, cp);  
                object[] newrow = new object[5];  
                // ('REC129-1','REC129-2',129,1290,'129.645')  
                newrow[cp[0]] = "REC129-1";  
                newrow[cp[1]] = "REC129-2";  
                newrow[cp[2]] = 129;  
                newrow[cp[3]] = 1290;  
                newrow[cp[4]] = 129.645M;  
                ds.Tables[0].Rows.Add(newrow);                  
                int z = hfda.Update(ds);  
                if (z != 1)  
                {  
                    logging.LogFail("a unexpected number of updates::"+z.ToString());  
                }  
                DataSet ds1 = new DataSet();  
                hfda.Fill(ds1);  
                int j = 0;  
                int i = 0;  
                foreach (DataRow row in ds1.Tables[0].Rows)  
                {  
                    string rec = (string)ds1.Tables[0].Rows[j][cp[0]];  
                    if (!rec.Equals("REC129-1"))  
                    {  
                        u.CompareValues((string)ds1.Tables[0].Rows[j][cp[0]], Datavals[i].OUT1_CHAR1, logging);  
                        u.CompareValues((string)ds1.Tables[0].Rows[j][cp[1]], Datavals[i].OUT1_CHAR2, logging);  
                        u.CompareValues((short)ds1.Tables[0].Rows[j][cp[2]], Datavals[i].OUT1_SMALLINT, logging);  
                        u.CompareValues((int)ds1.Tables[0].Rows[j][cp[3]], Datavals[i].OUT1_INTEGER, logging);  
                        u.CompareValues((decimal)ds1.Tables[0].Rows[j][cp[4]], Datavals[i].OUT1_DECIMAL, logging);  
                        j++;  
                        i++;  
                    }  
                    else  
                    {  
                        u.CompareValues((string)ds1.Tables[0].Rows[j][cp[0]], "REC129-1", logging);  
                        u.CompareValues((string)ds1.Tables[0].Rows[j][cp[1]], "REC129-2", logging);  
                        u.CompareValues((short)ds1.Tables[0].Rows[j][cp[2]], 129, logging);  
                        u.CompareValues((int)ds1.Tables[0].Rows[j][cp[3]], 1290, logging);  
                        u.CompareValues((decimal)ds1.Tables[0].Rows[j][cp[4]], 129.645M, logging);  
                        j++;  
                    }  
                }  
                if (j == 0)  
                {  
                    logging.LogFail("No Rows on DataTable!");  
                }  
                z = 0;  
                z = hfda.Update(dsold);  
                if (z != 1)  
                {  
                    logging.LogFail("a unexpected number of updates::" + z.ToString());  
                }  
                DataSet ds2 = new DataSet();  
                hfda.Fill(ds2);  
                u.ValidateDataSet(ds2, logging, Datavals, cp);  
  
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
 [Working with the Host File Adapter and Dataset](../core/working-with-the-host-file-adapter-and-dataset2.md)   
 [BizTalk Adapter for Host Files Configuration](../HIS2010/biztalk-adapter-for-host-files-configuration2.md)