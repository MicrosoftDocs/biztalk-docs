---
title: "PowerPivot (Excel)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2fee9af0-9c33-40fc-b7cd-68b435626486
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# PowerPivot (Excel)
PowerPivot for Excel is an add-in that you can use to perform powerful data analysis in Excel 2010, bringing self-service business intelligence to your desktop. Excel-based in-memory analysis overcomes existing limitations for massive data analysis on the desktop by using  efficient compression algorithms to load even the biggest data sets into memory. PowerPivot provides the following features:  
  
-   Data Analysis Expressions (DAX) is a new formula language that allows users to define custom calculations in PowerPivot tables (calculated columns) and in Excel PivotTables (measures). DAX puts powerful relational capabilities into the hands of users who want to create advanced analytics applications. It allows you to build new data relationships, and perform powerful manipulations aggregating data over billions of rows.  
  
-   SharePoint Integration features provide a secure environment for IT administrators to monitor and manage shared applications. SharePoint enables users to share data models and analysis, turning workbooks into shared applications that are accessible virtually any time and from any location.  
  
-   Support for multiple data sources enables you to load and combine data from any source or location, including relational databases, multidimensional sources, cloud services, data feeds, Excel files, text files, and data from the Web. This allows you to perform massive data analysis from multiple data sources on the desktop.  
  
-   PowerPivot Management Dashboard enables IT administrators to monitor and manage shared applications to ensure security, high availability, and performance.  
  
 PowerPivot for Excel includes a wizard that you can use to import data from different sources. Data is imported into PowerPivot for Excel as tables, which are shown as separate sheets in the PowerPivot window, similar to worksheets in an Excel workbook. But PowerPivot for Excel provides significantly different functionality from what is available in an Excel worksheet.  
  
 PowerPivot data is stored in an analytical database inside the Excel workbook, and a powerful local engine loads, queries, and updates the data in that database. You can create relationships between the tables in the PowerPivot window. Data is immediately available to PivotTables, PivotCharts, and other features in Excel that you use to aggregate and interact with data. All data presentation and interactivity are provided by Excel 2010. PowerPivot data and Excel presentation objects are contained within the same workbook (.xlsx, .xlsb, or .xlsm) file. PowerPivot supports files up to 2GB in size and enables you to work with up to 4GB of data in memory.  
  
 For more information on PowerPivot for Excel, see [PowerPivot Help](http://go.microsoft.com/fwlink/?LinkId=198239) (http://go.microsoft.com/fwlink/?LinkId=198239).  
  
## How to use PowerPivot with IBM DB2  
 These instructions demonstrate how to use PowerPivot for Excel to access information stored in an IBM DB2 relational database management system using the OLE DB Provider for DB2.  
  
1.  In the Excel window, on the **PowerPivot** tab, click **PowerPivot Window**.  
  
2.  In the **Connect to a Data Source** list, click **Others (OLEDB/ODBC)**, and then click **Next**.  
  
     The **Specify a Connection String** dialog appears.  
  
3.  In the **Friendly connection name** field, type **DB2sample**.  
  
4.  You can copy and paste an can copy and paste an OLE DB initialization string from the **Data Access Tool** to the **Connection String** edit box in the **Table Import Wizard**. Alternatively, you can build a new connection string, by clicking **Build**.  
  
     The Data Links Properties dialog appears.  
  
5.  Click the **Provider** tab, click **Microsoft OLE DB Provider for DB2**, and then click **Next**.  
  
6.  Click the **Provider** tab, click **Microsoft OLE DB Provider for DB2**, and then click **Next**.  
  
7.  In the **Connection** tab, click **Browse** to locate an existing UDL file. Alternatively, configure a new connection. For more information, see [Data Links (DB2)](../core/data-links-db2.md).  
  
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
 [Excel](../core/excel.md)   
 [External Data Sources (Excel)](../core/external-data-sources-excel.md)   
 [SharePoint](../core/sharepoint.md)