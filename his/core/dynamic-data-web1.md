---
title: "Dynamic Data Web1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a6492dd-2628-49e6-8a55-78ed43d05ffc
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Dynamic Data Web
This walkthrough demonstrates how you can create a basic Web site that uses ASP.NET Dynamic Data and a WCF Data Service. Dynamic Data enables you to create a data-driven Web site with little or no coding. WCF Data Services enables you to create and consume Open Data Protocol (OData) services in your application. You can use the Entity Provider for DB2 to generate Dynamic Data and WCF Data Services to access information stored in an IBM DB2 relational database. For more information, see [ASP.NET Dynamic Data Content Map](http://go.microsoft.com/fwlink/?LinkId=199029) (http://go.microsoft.com/fwlink/?LinkId=199029) and [WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=199030) (http://go.microsoft.com/fwlink/?LinkId=199030).  
  
 This topic contains the following sections:  
  
-   [Prerequisites](../core/dynamic-data-web1.md#pre)  
  
-   [Creating a Dynamic Data Web Site](../core/dynamic-data-web1.md#dyn)  
  
-   [Adding a Data Connection to Server Explorer](../core/dynamic-data-web1.md#con)  
  
-   [Adding Data to the Web Site](../core/dynamic-data-web1.md#web)  
  
-   [Registering the Data Context](../core/dynamic-data-web1.md#reg)  
  
-   [Testing the Dynamic Data Web Site](../core/dynamic-data-web1.md#test)  
  
##  <a name="pre"></a> Prerequisites  
 You must to install the following components in order to complete this walkthrough:  
  
-   Visual Studio 2012  
  
-   Internet Information Services 7  
  
-   IBM DB2 relational database server with a sample database such as SAMPLE, CORPDATA, or DSN8910.  
  
##  <a name="dyn"></a> Creating a Dynamic Data Web Site  
 Follow these steps to create Dynamic Data Web sites in Visual Studio with the ASP.NET Dynamic Data templates.  
  
1.  Start Visual Studio and from the **File** menu, click **New Web Site**. The New Web Site dialog box is displayed.  
  
2.  In the left pane under **Installed Templates**, select **Visual C#**.  
  
3.  In the center pane, select **ASP.NET Dynamic Data Entities Web Site**.  
  
4.  In the **Web location** box, select **File System** and then enter the name of the folder where you want to store the pages of the Web site. For example, type the folder name `C:\WebSites\DynamicData` and click **OK**.Visual Studio creates the Web site.  
  
##  <a name="con"></a> Adding a Data Connection to Server Explorer  
 In Visual Studio, the Server Explorer displays database connections beneath the Data Connections node. Follow these steps to open a database connection, retrieve and manipulate data.  
  
1.  On the **Tools** menu, select **Connect to Database**. The **Add Connection** dialog box is displayed.  
  
2.  Click **Change**. The Change Data Source dialog box is displayed. Click **DB2 Database**, and then click **OK**.  
  
3.  Click **Configure**. The Data Source dialog box of the Data Source Wizard is displayed.  
  
4.  In the **Data source platform**, select **DB2/NT**, and then click **Next**. The TCP/IP Network Connection dialog box is displayed.  
  
5.  In the **Address or alias** box, enter `127.0.0.1`. In the **Port** box, enter `50000`, and then click **Next**. The DB2 Database dialog box is displayed.  
  
6.  In the **Initial Catalog** box, enter `SAMPLE`. In the **Package collection** box, enter `NULLID`. In the **Default schema** and **Default qualifier** boxes, enter `DB2ADMIN`, and then click **Next**. The Locale dialog box is displayed.  
  
    > [!NOTE]
    >  When generating an entity model using the Entity Data Model Tools in Visual Studio, you must specify a value for the Default Qualifier connection property of the underlying MsDb2Client ADO.NET Framework Provider for DB2, which allows the provider to fetch the correct scope of DB2 catalog (tables, views, stored, procedures, columns and parameters) based on the target DB2 schema (collection).  
  
7.  In the **Host CCSID** list, select **ANSI – Latin (1252)**, and then click **Next**. The Security dialog box is displayed.  
  
8.  In the User name box, enter `db2admin`. In the **Password** and **Password confirmation** boxes, enter `Pass@word1`, and then click **Next**. The Advanced Options dialog box is displayed.  
  
9. Click **Next**. The All Properties dialog box is displayed.  
  
10. Click **Next**. The Validation dialog box is displayed.  
  
11. Click **Connect**, click **Packages**, click **Sample Query**, and then click **Next**. The Data Link Properties dialog box closes, and the new data connection appears beneath the Data Connections node, named for the server and database accessed.  
  
12. In the **Add Connection** dialog box, type `DB2` for Data source name.  
  
13. Click **Test Connection**, click **OK**, and then click **OK**.  
  
14. Optionally, in the **Server Explorer**, expand **Data Connections**, and view the database tables.  
  
##  <a name="web"></a> Adding Data to the Web Site  
 Follow these steps to add a database connection to the project. Later you will use the database to create a data context (classes to represent database entities) and then register the data context for use by Dynamic Data.  
  
1.  In **Solution Explorer**, right-click the project, click **New Item**. The Add New Item dialog box is displayed.  
  
2.  In the left pane under **Installed Templates**, select **Visual C#**. In the center pane, select **ADO.NET Entity Data Model**.  
  
3.  In the **Name** box, enter a name for the database model. For example, enter the name `DB2.edmx`.  
  
4.  Click **Add**. The create an App_Code folder dialog box is displayed.  
  
5.  Click **Yes**. The Choose Model Contents dialog box of the Entity Data Model Wizard is displayed.  
  
6.  Select **Generate from database**, and then click **Next**. The Choose Your Data Connection dialog box is displayed.  
  
7.  In the drop-down list, select the connection that you configured above. For example, select **DB2.SAMPLE.DB2ADMIN**. Click **Yes** to include the sensitive data (user name and password) in the connection string, and then click **Next**. The Choose Your Database Objects dialog box appears.  
  
8.  Click the triangle to expand the **Tables** node. Click the check box for **DEPARTMENT** and **EMPLOYEE** tables, and then click **Finish**. The ADO.NET Entity Data Model Designer is displayed.  
  
9. In the **Solution Explorer**, open the **DB2.Designer.cs** file that is located under the DB2.edmx file node. Notice that the **DB2.edmx** file contains the **SAMPLEEntities** class that represents the database. It also contains entity classes that represent database tables.  
  
10. In **Solution Explorer**, open the **web.config** file. Notice that the **connectionStrings** element contains the connection string to the DB2 database.  
  
11. Close the class file and the **web.config** file.  
  
##  <a name="reg"></a> Registering the Data Context  
 Follow these steps to register the data context for use by Dynamic Data.  
  
1.  In the **Solution Explorer**, open the **Global.asax** file.  
  
2.  Uncomment the line that contains the **DefaultModel.RegisterContext** method.  
  
3.  Set the appropriate context type, and set the variable **ScaffoldAllTables** to true.  
  
    ```  
    DefaultModel.RegisterContext(typeof(SAMPLEModel.SAMPLEEntities), new ContextConfiguration() { ScaffoldAllTables = true });  
    ```  
  
     This registers the data context for use by Dynamic Data and enables scaffolding for the data model.  
  
    > [!IMPORTANT]
    >  Enabling scaffolding by setting the variable **ScaffoldAllTables** to true can pose a security risk because you are exposing all the tables in the data model for display and edit operations. For more information, see [ASP.NET Dynamic Data Scaffolding](http://go.microsoft.com/fwlink/?LinkId=199054) (http://go.microsoft.com/fwlink/?LinkId=199054).  
  
4.  In the File menu, click **Save Global.asax**.  
  
##  <a name="test"></a> Testing the Dynamic Data Web Site  
 Follow these steps to test the Dynamic Data Web site that you have created.  
  
1.  In the **Debug** menu, click **Start Debugging**. If prompted to enable debugging, click **OK**. Internet Explorer displays the Dynamic Data Web site.  
  
2.  Click the **DEPARTMENTs** hyperlink to view the DB2 table.  
  
3.  Click the hyperlinks to navigate the model over the database. Optionally, click **Edit**, **Update**, **Delete** to make changes to the database through the Entity Provider for DB2.  
  
4.  A page is displayed that contains the data from the table that you selected. For tables that contain foreign key fields, a link is provided to the details page of the referenced table. If the table is a parent table in a one-to-many relationship, a link is provided to the list page of the child table.  
  
     Close the browser when you have finished navigating the database and editing records.  
  
## See Also  
 [WCF Data Service](../core/wcf-data-service1.md)   
 [Entity Framework](../core/entity-framework2.md)