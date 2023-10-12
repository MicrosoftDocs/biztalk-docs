---
description: "Learn more about: How to Enrich BAM Data Using Lookups"
title: "How to Enrich BAM Data Using Lookups"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Enrich BAM Data Using Lookups
There are cases in which the data that is available at operation time does not contain everything you need for reporting purposes. For example, you may have a ProductID but not a ProductName at runtime. Since the BAM Activity represents an abstraction independent of how the data is actually collected, it should contain an item named as the final data that you want to see in the report "ProductName". Just like any other item, you can use this in interpretive constructs such as milestone groups, durations, dimensions, and measures. Since the ProductName is not available at runtime, you must get some additional data that is sufficient for performing a lookup, such as the ProductID.  
  
 You should collect the data in the same column, instead of the data that you need for reports. For example, you should collect the ProductID instead of ProductName at runtime. If more columns are required, you may create more items in the activity but not use them in any View.  
  
### To enrich BAM data via lookups  
  
1.  Deploy your BAM definition.  
  
2.  In SQL Server Management Studio, add the server that contains the data of interest as a remote server.  
  
3.  Locate the data analysis package named BAM_AN_`<View Name>`. For example if the view is SalesMgr, this will be BAM_AN_SalesMgr.  
  
4.  Set the zoom to magnify the view of the package (e.g. 100%)  
  
5.  Add a SQL connection that you will be using in the lookups.  
  
6.  Locate the transform data task after the step "Cleanup Staging". This is where you move the data from the PrimaryImport to the StarSchema database. There are two instances of this task—one for the completed activities, and another for the one that is in progress. Apply all the rest of the steps to both tasks.  
  
7.  Click the transformation.  
  
8.  Select Lookups; add your lookup "LookupProductByID" using the lookup connection (see SQL books online for lookups). If for example the lookup is a simple table "LookupProduct", the with columns ProductID and ProductName, the text of the lookup will be:  
  
    ```  
    SELECT ProductName  
    FROM   LookupProduct  
    WHERE ProductID=?  
    ```  
  
9. Click the Transformations tab. Delete the default data transformation "Transform", and create ActiveX transformation instead. Click Source Columns and add all columns. Click Destination Columns and add all columns.  
  
10. Click the General tab, and then Properties. This results in automatic generation of a script that performs the trivial copy transformation as shown:  
  
    ```  
    Function Main()  
       ...  
       DTSDestination("ProductName") = DTSSource("ProductName")  
       ...  
       Main = DTSTransformStat_OK  
    End Function  
    ```  
  
11. Change the value by using the lookup as shown:  
  
    ```  
    Function Main()  
       ...  
       DTSDestination("Product")= _  
                      DTSLookups( "LookupProductByID" ).Execute(  _                                  DTSSource("Product"))  
       ...  
       Main = DTSTransformStat_OK  
    End Function  
    ```  
  
12. Save and then run the package.  
  
13. Ensure that the correct data ends up in the OLAP cube. You should save the package as VBScript or a structured storage file, because it contains your custom code, not just the auto-generated steps from BAM.  
  
> [!NOTE]
>  The lookup works only for the scheduled reports that you perform with DTS and OLAP. If you need different data than what is collected in the real-time aggregation, then you must retrieve the data before calling the BAM API.  
  
## See Also  
 [Using Business Activity Monitoring](../core/using-business-activity-monitoring.md)   
 [Deploying Localized BAM XML Files](../core/deploying-localized-bam-xml-files.md)
