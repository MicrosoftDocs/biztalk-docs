---
title: "Excel data sources | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf666c62-b34d-40f7-9824-f162bb92dafd
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Excel as a data source - HIS

## Overview
Excel is a spreadsheet program in the Microsoft Office system. You can use Excel to create and format workbooks (a collection of spreadsheets) in order to analyze data and make more informed business decisions. You can use Excel to track data, build models for analyzing data, write formulas to perform calculations on that data, pivot the data in numerous ways, and present data in a variety of professional looking charts.  
  
 Excel includes many features, such as slicers that allow you to interactively filter your data, and enhancements to existing features such as pivot tables. In addition, the Excel and the SQL Server teams have collaborated to create a PowerPivot, a powerful data analysis tool made up of two components: an add-in for Excel and a series of  features for SharePoint. 

## External Data Sources (Excel)
You can use Excel to connect to data from many different data sources and locations, including relational databases, multidimensional sources, cloud services, data feeds, Excel files, text files, and data from the Web. The main benefit of connecting to external data is that you can periodically analyze this data without repeatedly copying the data to your workbook, which is an operation that can be time consuming and prone to error. After connecting to external data, you can also automatically refresh (or update) your Excel workbooks from the original data source whenever the data source is updated with new information.  
  
 Connection information is stored in the workbook and can also be stored in a connection file, such as an Office Data Connection (ODC) file or a Data Source Name file (DSN). We recommend that you use ODC files for connecting to external data from Excel.  
  
 **Office Data Connection (ODC) files**  
  
 You can create ODC files by connecting to external data through the **Select Data Source** dialog box or by using the Data Connection Wizard to connect to new data sources. An ODC file uses custom HTML and XML tags to store the connection information. You can easily view or edit the ODC file in Excel.  
  
 You can convert other connection files, such as DSN, UDL, and query files, to an ODC file by opening the connection file and then clicking the **Export Connection File** button on the **Definition** tab of the **Connection Properties** dialog box.  
  
### Excel and the OLE DB Provider for DB2  
Use the following steps to access information stored in an IBM DB2 database using the OLE DB Provider for DB2.  
  
1.  On the **Data** tab, in the **Get External Data** group, click **From Other Data Sources**, and then click **From Data Connection Wizard**. The **Data Connection Wizard** dialog box appears.  
  
2.  In the **What kind of data source do you want to connect to** list, click **Other/Advanced**, and then click **Next**. The **Data Link Properties** dialog box appears.  
  
3.  In the **Provider** tab, click **Microsoft OLE DB Provider for DB2**, and then click **Next**.  
  
4.  In the Connection tab, configure the network, authentication, and system information. 
  
     Click **Test Connection**, and then click **OK**. The **Select Database and Table** of the **Data Connection Wizard** dialog box appears.  
  
5.  In the **Select Database and Table** dialog, click the host file that you want to access from the **Connect to a specific table** list, and then click **Next**. The **Save Data Connection File and Finish** dialog appears.  
  
6.  In the **Save Data Connection File and Finish** dialog, click **Save password in file**. The Microsoft Excel warning dialog appears.  
  
7.  In the warning dialog, click **Yes**, and then click **Finish**. The **Import Data** dialog appears.  
  
8.  In the Import Data dialog, click **Properties**. The **Connection Properties** dialog appears.  
  
9. In the **Connection Properties** dialog, click **Definition** to see the Connection string, Command type, and Command text, and then click **OK**.  
  
10. In the Import Data dialog, click **OK**.  

## PowerPivot for Excel
PowerPivot for Excel is an add-in that you can use to perform powerful data analysis in Excel, bringing self-service business intelligence to your desktop. Excel-based in-memory analysis overcomes existing limitations for massive data analysis on the desktop by using  efficient compression algorithms to load even the biggest data sets into memory. PowerPivot provides the following features:  
  
- Data Analysis Expressions (DAX) is a new formula language that allows users to define custom calculations in PowerPivot tables (calculated columns) and in Excel PivotTables (measures). DAX puts powerful relational capabilities into the hands of users who want to create advanced analytics applications. It allows you to build new data relationships, and perform powerful manipulations aggregating data over billions of rows.  
  
- SharePoint Integration features provide a secure environment for IT administrators to monitor and manage shared applications. SharePoint enables users to share data models and analysis, turning workbooks into shared applications that are accessible virtually any time and from any location.  
  
- Support for multiple data sources enables you to load and combine data from any source or location, including relational databases, multidimensional sources, cloud services, data feeds, Excel files, text files, and data from the Web. This allows you to perform massive data analysis from multiple data sources on the desktop.  
  
- PowerPivot Management Dashboard enables IT administrators to monitor and manage shared applications to ensure security, high availability, and performance.  
  
  PowerPivot for Excel includes a wizard that you can use to import data from different sources. Data is imported into PowerPivot for Excel as tables, which are shown as separate sheets in the PowerPivot window, similar to worksheets in an Excel workbook. But PowerPivot for Excel provides significantly different functionality from what is available in an Excel worksheet.  
  
  PowerPivot data is stored in an analytical database inside the Excel workbook, and a powerful local engine loads, queries, and updates the data in that database. You can create relationships between the tables in the PowerPivot window. Data is immediately available to PivotTables, PivotCharts, and other features in Excel that you use to aggregate and interact with data. All data presentation and interactivity are provided by Excel 2010. PowerPivot data and Excel presentation objects are contained within the same workbook (.xlsx, .xlsb, or .xlsm) file. PowerPivot supports files up to 2GB in size and enables you to work with up to 4GB of data in memory.  
  
See [Power Pivot: Powerful data analysis and data modeling in Excel](https://support.office.com/article/Power-Pivot-Powerful-data-analysis-and-data-modeling-in-Excel-A9C2C6E2-CC49-4976-A7D7-40896795D045).  
  
### Use PowerPivot with IBM DB2  
The following steps show you how to use PowerPivot for Excel to access information stored in an IBM DB2 relational database management system using the OLE DB Provider for DB2.  
  
1.  In the Excel window, on the **PowerPivot** tab, click **PowerPivot Window**.  
  
2.  In the **Connect to a Data Source** list, click **Others (OLEDB/ODBC)**, and then click **Next**.  
  
     The **Specify a Connection String** dialog appears.  
  
3.  In the **Friendly connection name** field, type **DB2sample**.  
  
4.  You can copy and paste an can copy and paste an OLE DB initialization string from the **Data Access Tool** to the **Connection String** edit box in the **Table Import Wizard**. Alternatively, you can build a new connection string, by clicking **Build**.  
  
     The Data Links Properties dialog appears.  
  
5.  Click the **Provider** tab, click **Microsoft OLE DB Provider for DB2**, and then click **Next**.  
  
6.  Click the **Provider** tab, click **Microsoft OLE DB Provider for DB2**, and then click **Next**.  
  
7.  In the **Connection** tab, click **Browse** to locate an existing UDL file. Alternatively, configure a new connection. For more information, see [Data Links (DB2)](../core/data-links-db2-2.md).  
  
     Click **Test**, and then click **OK**.  
  
     The **Select Database and Table** of the **Data Connection Wizard** dialog box appears.  
  
8.  Once you have specified a connection string, click **Next**.  
  
     The **Choose How to Import the Data** dialog appears.  
  
9. You can select from a list of tables or you can write a query (using Command type = Text). Click the first option (Select from a list of tables and views to choose the data to import), and then click **Next**.  
  
     The **Select Tables and Views** dialog appears.  
  
10. In the **Source Table** list, click a table, and then click **Preview & Filter**.  
  
     The **Preview Selected Table** dialog appears.  
  
11. Use the **checkbox** to select or deselect columns. Use the **drop-down arrow** to filter on values, and then click **OK**.  
  
12. Review your selections. If everything looks good, then click **Finish**.  
  
     The **Importing** dialog appears.  
  
13. In **Importing** dialog, review the **Status** for each listed **Work Item**, and then click **Close**.  
  
14. In the PowerPivot for Excel window, click the Design tab, to see options for creating and managing relationships between tables.  

## See Also  
 [Office](../core/office2.md)   
 [SharePoint](../core/sharepoint1.md)   
 [SQL Server](../core/sql-server2.md)