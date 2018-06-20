---
title: "Managing the Bicplus Table in the A4SWIFT Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Bank Identifier Code (BIC), Bicplus table"
  - "A4SWIFT database, Bicplus table"
  - "Bicplus table"
ms.assetid: a255cdea-5ed4-4481-97f1-8425877a76d6
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing the Bicplus Table in the A4SWIFT Database
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] uses a table of BIC entries to perform BIC validation. This table can be either the Bicplus table in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database or a table in a custom database.  
  
 To manage this table, you must populate it with BIC values from SWIFT. If you use a custom database, you must also export SQL views in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database into the custom database.  
  
## Importing BIC data from the SWIFT Bicplus database  
 You must populate the table of BIC entries (either the default or the custom table) with BIC values from SWIFT. The SWIFT BIC data is available in an [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] spreadsheet or in an Oracle database that is updated monthly. For more information about SWIFT BIC data, go to [http://go.microsoft.com/fwlink/?LinkId=27885](http://go.microsoft.com/fwlink/?LinkId=27885).  
  
 If you use a custom database, you must export BIC data from the SWIFT Bicplus database into the custom database. You must  
  
 You can import data from the BIC [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] spreadsheet provided by SWIFT into the Bicplus table in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database, because they are compatible. If you import the data from the SWIFT spreadsheet into a non-[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database, make sure that the fields and columns in your database, particularly the BIC column, are compatible with the SWIFT spreadsheet.  
  
 The import operation does not remove any unpublished BIC codes when it updates the destination table with the codes published in the SWIFT table.  
  
 The changes made to the Bicplus table of the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database are logged in the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] log file.  
  
#### To import BIC data from the SWIFT Bicplus database  
  
1. Click **Start**, point to **All Programs**, point to the inistalled version of SQL Server, and then click **SQL Server Management Studio**.  
  
2. In the Connect to Server dialog box, click **Connect**.  
  
3. In the Microsoft SQL Server Management Studio window, expand your server node, and then **Databases**.  
  
4. Right-click **A4SWIFT**, point to **Tasks**, and then click **Import Data**.  
  
5. On the SQL Server Import and Export Wizard welcome page, click **Next**.  
  
6. On the **Choose a Data Source** page, if importing BIC data from the SWIFT Bicplus [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] spreadsheet, select **Microsoft Excel** in the **Data Source** text box. Browse to the location of the spreadsheet, and select the file name of the spreadsheet in the **Excel file path** text box. Click **Next**.  
  
    If importing BIC data from the Oracle database, select **Microsoft ODBC Driver for Oracle** in the **Data Source** text box. Enter the server with the Oracle database, and the user name and password required to connect to that server, and then click **Next**.  
  
7. On the **Choose a Destination** page, verify that **Microsoft OLE DB Provider for SQL Server** is entered in the **Destination** text box, and that **Use Windows Authentication** is selected. If you are populating the Bicplus table in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database, verify that **A4SWIFT** is entered in the **Database** text box. If you are using a custom database, enter the name of that database in the **Database** text box. Click **Next**.  
  
8. On the **Select Table Copy or Query** page, verify that **Copy data from one or more tables or views** is selected. If you need to use a query to specify the data, select **Write a query to specify the data to transfer**. Click **Next**.  
  
9. On the **Select Source Tables and Views** page, click **Bicplus** in the **Source** column, select **Bicplus** in the **Destination** column, and then click **Next**.  
  
10. On the **Save and Execute Package** page, enter the appropriate schedule information, and then click **Next**.  
  
11. On the **Complete the Wizard** page, review the summary and then click **Finish**.  
  
## Importing SQL views from the A4SWIFT database into a Custom Database  
 The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] setup program installs two SQL views in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database. One view is for eight-character BICs and the other is for 11-character BICs.  
  
 If you use a custom database instead of the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database, you must importing these SQL views into the custom database. You do so by executing the CreateBICViews.sql script in the Query Analyzer. This script is in \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT/Scripts.  
  
#### To import SQL views from the A4SWIFT database into a custom database  
  
1.  In Windows Explorer, move to \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\Scripts. Double-click **CreateBICViews.sql**.  
  
2.  In the Connect to Server dialog box, click **Connect**.  
  
3.  In the Microsoft SQL Server Management Studio window, select **A4SWIFT** in the database text box.  
  
4.  In the query pane, if you are storing BICs in a table that is named other than "Bicplus", find **dbo.Bicplus** in the view **dbo.Bic11**, and change it to the appropriate table name. Do the same for the view **dbo.Bic8**.  
  
5.  If you are storing BICs in a column that is named other than "BIC", find **BIC** in the **SELECT**, **WHERE**, and **ORDER BY** clauses, and change it to the appropriate column name.  
  
6.  Click **Execute**.  
  
## See Also  
 [Enabling Validation of Bank Identifier Codes](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)