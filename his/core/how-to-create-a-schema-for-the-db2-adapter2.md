---
title: "How to Create a Schema for the DB2 Adapter2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb75b20e-6a3a-4d64-b116-b58386b1f85b
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a Schema for the DB2 Adapter
To create the XSD schemas for the BizTalk Adapter for DB2, you use the DB2 Schema Generation Wizard.  
  
### To generate the DB2 schema  
  
1.  Open your BizTalk Visual Studio project.  
  
2.  Right-click the project, point to **Add**, and then click **Add Generated Items**, and then click **Add**.  
  
3.  In the **Add Generated Items** dialog box, select **Add Adapter Metadata**.  
  
     This starts the Add Adapter Wizard.  
  
4.  On the **Select Adapter** page, select **DB2**.  
  
5.  In the Port list, select a configured Send Port or Receive Location, and then click Next.  
  
     This starts the DB2 Adapter Schema Generation Wizard.  
  
6.  On the **Database Information** page, create a connection string, or select an existing connection string.  
  
7.  On the **Schema Information** page, define the default namespace, root elements, and port type to be used in the schema.  
  
     If you select **Receive port**, only a request document root element name is needed. If you select **Send port**, both request and response document root element names are required.  
  
8.  On the **Statement Type Information** page, select the type of database command to be issued.  
  
     If you selected receive ports on the previous page, you can choose either a SELECT SQL statement or a stored procedure. If you selected send ports on the previous page, you can choose to issue an updategram, stored procedure, or SELECT statement.  
  
9. On the **Statement Information** page, enter the details about the DB2 database.  
  
     Depending on the information entered on earlier pages, the following properties are available:  
  
    1.  **Receive Select Statement** in the **Statement Information** dialog, type a SQL SELECT statement in the **SQL script** edit box. Optionally, click **Browse** to load a text file containing a statement.  
  
    2.  **Receive Stored Procedure** in the **Statement Information** dialog, click a **Stored procedure name**. In the Parameters list, click the **Value** checkbox for each parameter required.  
  
    3.  **Send Updategram** in the **Statement Information** dialog, click a **Table name**. In the **Parameters** list, click the **Value** checkbox for each column required. When using **BulkCopy**, you must click each **Value** checkbox to select all columns.  
  
    4.  **Send Stored Procedure** in the **Statement Information** dialog, click a **Stored procedure name**. In the **Parameters** list, click the **Value** checkbox for each parameter required.  
  
    5.  **Send Select Statement** in the statement Information dialog, type SQL SELECT statement in the SQL script edit box. Optionally, click **Browse** to load a text file containing a statement.  
  
10. On the **Completing the DB2 Transport Schema Generation Wizard** page, click **Finish**.  
  
## See Also  
 [BizTalk Adapter for DB2 Configuration](../core/biztalk-adapter-for-db2-configuration1.md)   
 [Data Source Wizard (DB2)](../core/data-source-wizard-db2-2.md)