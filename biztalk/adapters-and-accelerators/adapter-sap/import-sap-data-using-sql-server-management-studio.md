---
title: "Import SAP Data Using SQL Server Management Studio | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "importing SAP data, how to"
  - "SQL Server Management Studio, importing data"
ms.assetid: c8151c6d-4b33-40fe-9b83-9bed27df9a99
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Import SAP Data Using SQL Server Management Studio
This section provides information on how to use the SQL Server Management Studio to import data from an SAP system into a SQL Server database. This section provides instruction on how to create an SSIS package that you can execute to import data. This section also provides information on how to execute the SSIS package.  
  
## Prerequisites  
 Before performing the procedures provided in this topic, make sure:  
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] is installed on the computer.  
  
- SQL Server Business Intelligence Development Studio is installed on the computer.  
  
### To import data using SQL Server Management Studio  
  
1. Start the SQL Server Management Studio.  
  
2. In the **Connect to Server** dialog box, specify the values to connect to a SQL Server database and click **Connect**. The **Microsoft SQL Server Management Studio** opens.  
  
3. In the **Object Explorer**, expand the SQL Server name, expand **Databases**, and right-click the database into which you will be exporting the tables from the SAP system. From the context menu, point to **Tasks**, and click **Import Data**. This starts the **SQL Server Import and Export Wizard**.  
  
4. Read the information on the welcome screen and click **Next**.  
  
5. In the **Choose a Data Source** dialog box, from the **Data Source** drop-down list **.NET Framework Data Provider for mySAP Business Suite**. The dialog box lists the different connection parameters to connect to an SAP system. A typical connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires:  
  
   - The connection parameters for a connection type. The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports connection types A, B, and D. To connect to an SAP system you must provide connection parameters for any *one* of these connection types. For example, for connection type A, you must provide the name of the application server host and the system number.  
  
   - The login information to connect to an SAP system such as username and password.  
  
     For more information about the connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Read about Data Provider for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).  
  
     In the **Choose a Data Source** dialog box, specify:  
  
   - The connection parameters for any one connection type.  
  
   - The login information to connect to an SAP system.  
  
   - Whether you want to enable SAP GUI debugging.  
  
   - Whether you want to use RFC SDK tracing.  
  
     Click **Next**.  
  
6. In the **Choose a Destination** dialog box:  
  
   1.  From the **Destination** drop-down list, select **SQL Native Client**.  
  
   2.  From the **Server name** drop-down list, select a SQL server name.  
  
   3.  Select an authentication mode.  
  
   4.  From the **Database** drop-down list, select the database to which you want to import the SAP table.  
  
   5.  Click **Next**.  
  
7. In the **Specify Table Copy or Query** dialog box, choose the **Write a query to specify the data to transfer** option and click **Next**.  
  
8. In the **Provide a Source Query** dialog box, specify a SELECT query to filter the data to be imported into the SQL Server. For more information about the grammar for a SELECT query for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Syntax for a SELECT Statement SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).  
  
    Click the **Parse** button to validate the query and click **OK** in the pop-up dialog box. Click **Next**.  
  
9. In the **Select Source Tables and Views** dialog box, select the check box against the source and destination tables. The source is the query you specified to retrieve data from SAP. The destination is the table that will be created in the SQL Server database.  
  
10. The wizard creates a default mapping between the source and destination table fields. However, you can change the mappings according to your requirement. To change the field mappings, click **Edit Mappings**.  
  
     ![Column mappings between SAP and SQL tables](../../adapters-and-accelerators/adapter-sap/media/73751f74-4cd0-47c6-85ea-de7f507131a0.gif "73751f74-4cd0-47c6-85ea-de7f507131a0")  
  
11. In the **Column Mappings** dialog box, you can:  
  
    -   Change the names of columns in the destination table.  
  
    -   Ignore certain columns in the destination table.  
  
    -   Change the data type for fields in destination table.  
  
    -   Change other field attributes such as nullable, size, precision, and scale.  
  
    -   Click **OK**.  
  
12. In the **Select Source Tables and Views** dialog box, click **Next**.  
  
13. In the **Save and Execute Package** dialog box,  
  
    - Select the **Execute immediately** check box to execute the query.  
  
    - Select the **Save SSIS Package** check box to save the query as a package and execute it later. If you chose to save the package, you must also specify whether you want to save the package in the SQL Server or the file system.  
  
    - From the **Package protection level** drop-down list, select a protection level for the package and specify credentials where required.  
  
    - Click **Next**.  
  
      If you chose to save the package, proceed to next step. Otherwise, skip to step 15.  
  
14. In the **Save SSIS Package** dialog box, specify:  
  
    -   Name for the package  
  
    -   Description for the package  
  
    -   If you chose to save the package to a SQL server, select a SQL Server from the **Server name** drop-down list.  
  
    -   If you chose to save the package to the file system, specify the name and location of the file in the **File name** text box.  
  
    -   Click **Next**.  
  
15. In the **Complete the Wizard** dialog box, review the summary of actions that the wizard will perform, and click **Finish**.  
  
16. In the **Performing Operations** dialog box, the wizard starts executing tasks to import the information from SAP into a SQL Server database table. The status for each task is displayed in the wizard.  
  
17. After all the tasks are successfully executed, click **Close**. If a task fails, see the corresponding error message, fix the issue, and rerun the wizard.  
  
## Running the SSIS Package  
 If you chose to save the SSIS package, you can run it to retrieve the most recent information from the SAP system. This section provides information on how to run the package if you chose to save it to the file system.  
  
#### To run the package from Windows Explorer  
  
1. From the **Windows Explorer**, navigate to the location where you saved the package, and double-click the package.  
  
2. On the **Execute Package Utility** dialog box, click **Execute**.  
  
3. The **Package Execution Progress** dialog box displays the progress of the different tasks.  
  
4. After all the tasks are successfully executed, click **Close**.  
  
5. On the **Execute Package Utility** dialog box, click **Close**.  
  
   For more information about running packages, see [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972). For any other information related to SSIS packages, see [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).  
  
## Verifying the Results  
 After executing the package, you must verify the results by going to the SQL Server database to which the SAP data is imported. Executing the package should have created a table in destination database and populated with the values from the SAP table.  
  
## See Also  
 [Using the Data Provider for SAP with SSIS](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)