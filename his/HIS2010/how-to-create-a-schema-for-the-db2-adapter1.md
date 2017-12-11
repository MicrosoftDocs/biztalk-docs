---
title: "How to Create a Schema for the DB2 Adapter1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3e93b0d-c640-439e-8c6b-3cf6a94a9aa0
caps.latest.revision: 4
---
# How to Create a Schema for the DB2 Adapter
To create the XSD schemas for the BizTalk Adapter for DB2, you use the DB2 Schema Generation Wizard.  
  
### To generate the DB2 schema  
  
1.  Open your BizTalk Visual Studio project.  
  
2.  Right-click the project, point to **Add**, and then click **Add Generated Items**.  
  
3.  In the **Add Generated Items** dialog box, select **Add Adapter Metadata**.  
  
     This starts the Add Adapter Wizard.  
  
4.  On the **Select Adapter** page, select **DB2**, and then click **Next**.  
  
     This starts the DB2 Adapter Schema Generation Wizard.  
  
5.  On the **Database Information** page, create a connection string, or select an existing connection string.  
  
     This can be Initial Catalog, Package Collection, (TCP Address and Port) or (APPC Local LU, Remote LU, and Mode), (User Name and Password), or (Integrated Security). Maximum length is 1024.  
  
6.  On the **Schema Information** page, define the default namespace, root elements, and port type to be used in the schema.  
  
     If you select **Receive port**, only a request document root element name is needed. If you select **Send port**, both request and response document root element names are required.  
  
7.  On the **Statement Type Information** page, select the type of database command to be issued.  
  
     If you selected receive ports on the previous page, you can choose either a SELECT SQL statement or a stored procedure. If you selected send ports on the previous page, you can choose to issue an updategram, stored procedure, or SELECT statement.  
  
8.  On the **Statement Information** page, enter the details about the DB2 database.  
  
     Depending on the information entered on earlier pages, the following properties are available:  
  
    1.  **Receive Select Statement** If you chose to use a receive port with an SQL statement, you can either select, or browse to, the statement here.  
  
    2.  **Receive Stored Procedure** If you chose to use a receive port and issue a stored procedure, you can select a stored procedure from the current connection’s catalog. You must enter values for all parameters on this page.  
  
    3.  **Send Updategram** If you chose to use a send port and updategrams, you can select an updategram operation here, and also the table and columns that will be present in the updategram.  
  
    4.  **Send Stored Procedure** If you chose to use a send port and issue a stored procedure, you can select a stored procedure from the current connection’s catalog. You do not have to enter values for all parameters on this page.  
  
    5.  **Send Select Statement** If you chose to use a send port with an SQL SELECT statement, you can either select, or browse to, the statement here.  
  
9. On the **Completing the DB2 Transport Schema Generation Wizard** page, click **Finish**.  
  
## See Also  
 [BizTalk Adapter for DB2 Configuration](../HIS2010/biztalk-adapter-for-db2-configuration2.md)   
 [Data Access Library Programmer's Guide &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/73ba0edf-74d4-44d5-b018-47f9f88dddf2)   
 [Managed Provider for DB2 Programmer's Guide](../HIS2010/managed-provider-for-db2-programmer-s-guide1.md)