---
title: "External Data Sources (Excel)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f616e2a9-7ccf-4dc9-85c5-7ef0ab9baa88
caps.latest.revision: 4
---
# External Data Sources (Excel)
You can use Excel to connect to data from many different data sources and locations, including relational databases, multidimensional sources, cloud services, data feeds, Excel files, text files, and data from the Web. The main benefit of connecting to external data is that you can periodically analyze this data without repeatedly copying the data to your workbook, which is an operation that can be time consuming and prone to error. After connecting to external data, you can also automatically refresh (or update) your Excel workbooks from the original data source whenever the data source is updated with new information.  
  
 Connection information is stored in the workbook and can also be stored in a connection file, such as an Office Data Connection (ODC) file or a Data Source Name file (DSN). We recommend that you use ODC files for connecting to external data from Excel.  
  
 **Office Data Connection (ODC) files**  
  
 You can create ODC files by connecting to external data through the **Select Data Source** dialog box or by using the Data Connection Wizard to connect to new data sources. An ODC file uses custom HTML and XML tags to store the connection information. You can easily view or edit the ODC file in Excel.  
  
 You can convert other connection files, such as DSN, UDL, and query files, to an ODC file by opening the connection file and then clicking the **Export Connection File** button on the **Definition** tab of the **Connection Properties** dialog box.  
  
## Excel and the OLE DB Provider for DB2  
 These instructions demonstrate how to access information stored in an IBM DB2 database using the OLE DB Provider for DB2.  
  
1.  On the **Data** tab, in the **Get External Data** group, click **From Other Data Sources**, and then click **From Data Connection Wizard**. The **Data Connection Wizard** dialog box appears.  
  
2.  In the **What kind of data source do you want to connect to** list, click **Other/Advanced**, and then click **Next**. The **Data Link Properties** dialog box appears.  
  
3.  In the **Provider** tab, click **Microsoft OLE DB Provider for DB2**, and then click **Next**.  
  
4.  In the Connection tab, configure the network, authentication, and system information. For more information, see [Data Links (DB2)](http://msdn.microsoft.com/en-us/27f6b355-6eb2-451e-9a1a-855696c584be).  
  
     Click **Test Connection**, and then click **OK**. The **Select Database and Table** of the **Data Connection Wizard** dialog box appears.  
  
5.  In the **Select Database and Table** dialog, click the host file that you want to access from the **Connect to a specific table** list, and then click **Next**. The **Save Data Connection File and Finish** dialog appears.  
  
6.  In the **Save Data Connection File and Finish** dialog, click **Save password in file**. The Microsoft Excel warning dialog appears.  
  
7.  In the warning dialog, click **Yes**, and then click **Finish**. The **Import Data** dialog appears.  
  
8.  In the Import Data dialog, click **Properties**. The **Connection Properties** dialog appears.  
  
9. In the **Connection Properties** dialog, click **Definition** to see the Connection string, Command type, and Command text, and then click **OK**.  
  
10. In the Import Data dialog, click **OK**.  
  
## See Also  
 [Excel](../core/excel.md)