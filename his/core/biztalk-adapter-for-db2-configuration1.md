---
title: "Configure BizTalk Adapter for DB2 | Microsoft Docs"
description: Create a receive location, send port, and schema using the BizTalk Adapter for DB2 in Host Integration Server (HIS)
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9bbbaa5-a07a-491b-8539-3f6e5b257466
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# BizTalk Adapter for DB2 Configuration - HIS

## Overview
The Microsoft BizTalk Adapter for DB2 connects BizTalk Server to vital data stored in IBM mainframe DB2 for z/OS, IBM midrange DB2 for i5/OS, and IBM server DB2 running on Linux, UNIX and Windows operating systems. The adapter is based on the Microsoft ADO.NET Data Provider for DB2 and supports a broad range of functions, including send ports and receive ports with distributed transactions across SNA and TCP/IP network connections. Using SQL commands defined within port configuration wizards, IT professionals can easily create solutions that efficiently integrate DB2 databases without writing code.  

 The adapter serves two main functions:  

- For **Send** operations (both One Way and Solicit Response), the adapter sends SQL commands and stored procedures to a DB2 instance, with the option of soliciting a response.  

- For **Receive** operations (One Way only), the adapter creates an SQL command or stored procedure that polls DB2 objects and creates per-row messages, which are then submitted to the BizTalk message system.  

  In addition, the BizTalk Adapter for DB2 uses the standard BizTalk Adapter tracing tool as a troubleshooting mechanism.  

## Create a DB2 send port
Sign in with an account that is a member of the BizTalk Server Administrators group.

1. In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then select your application.

2. Right-click **Send Ports**, select **New**, and then select **Static One-way Send Port**.  

3. In the **Send Port Properties**, set the **Transport Type** to **DB2**. Select **Configure**, and enter the following properties:  


   |            Use this            |                                                                                                                                                                                                                                                                      To do this                                                                                                                                                                                                                                                                       |
   |--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |     **BulkCopyBatchSize**      |                                                                                                                                   The **BulkCopyBatchSize** property instructs the Adapter the number of rows to process per batch transaction. This **optional** property accepts an **integer** value. The default value is **20**. A value of **0** instructs the Adapter to process all rows in a single batch.                                                                                                                                   |
   |       **CommandTimeout**       |                                                                                                         The **CommandTimeout** property sets the wait time before the Adapter terminates an attempt to execute a command and then generate an error. This **optional** property accepts an **integer** value. The default value is **30** seconds. A value of 0 indicates no limit (an attempt to execute a command will wait indefinitely).                                                                                                          |
   |     **Connection String**      |                                                The name of a connection string that is used to connect to the DB2 database.<br /><br /> To configure a new or existing Connection String, click the ellipsis (**…**). This starts the Data Source Wizard.<br /><br /> To access Help, click **Help** on the wizard pages, or open the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Help and look in [Data Source Wizard (DB2)](../core/data-source-wizard-db2-2.md).                                                |
   |     **DB2 Set Registers**      | The **DB2 Set Registers** property instructs the Adapter to execute one or more SQL SET statements. This optional property accepts a **string** value. The default value is an **empty string**, which denotes no statement. The supported syntax is a semi-colon delimited list of SET statement commands with a comma separate list of SET statement values “\<SET command 1> space \<SET value 1> semi-colon; \<SET command 2> space \<SET value a> comma \<SET value b> semi-colon”). For example, enter “SET CURRENT PATH 'DSN8910', 'HISDEMO'”. |
   | **Document Target Namespace**  |                                                                                                                                                                                                                                     The target namespace that is used in the XML documents that are sent to DB2.                                                                                                                                                                                                                                      |
   | **Response Root Element Name** |                                                                                                                                                                                                         The root element name that is used in the XML documents that are received from DB2. (This property may be empty for a one-way port.)                                                                                                                                                                                                          |
   |            **URI**             |                                                                                                                                                                                                                              Uniform resource identifier. A name to identify the send port location. Default is DB2://.                                                                                                                                                                                                                               |
   |        **UseBulkCopy**         |                                                                                                                                                               The **UseBulkCopy** property instructs the Adapter to process send port INSERT commands in bulk copy mode to improve performance. This **optional** property accepts a **Boolean** value. The default value is **false**.                                                                                                                                                               |


4. Select **OK** to save your changes.

5. For the **Send Handler**, select the host instance to run the adapter, and select the **Send Pipeline**. 

6. Select **OK** to save your changes.

7. In the **Send Ports**, right-click your new send port, and select **Enlist** and then **Start**.  

## Create a DB2 receive port
Sign in with an account that is a member of the BizTalk Server Administrators group. 

1. In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then select your application.

2. Right-click **Receive Ports**, select **New**, and then select **One-way Receive Port**. Configure your properties, and select **OK**.  

3. Right-click **Receive Locations**, select **New**, and then select **One-way Receive Location**.  Select the receive port you just created, and then click **OK**.  

4. In the **Receive Location Properties**, set the **Transport Type** to **DB2**. Select **Configure**, and enter the following properties: 


   |            Use this            |                                                                                                                                                                                                                                                                To do this                                                                                                                                                                                                                                                                 |
   |--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |       **CommandTimeout**       |                                                                                                           The CommandTimeout property sets the wait time before the Adapter terminates an attempt to execute a command and then generate an error. This optional property accepts an integer value. The default value is 30 seconds. A value of 0 indicates no limit (an attempt to execute a command will wait indefinitely).                                                                                                            |
   |     **Connection String**      |                                          Enter the name of a connection string that will be used to connect to the DB2 database.<br /><br /> To configure a new or existing Connection String, click the ellipsis (**…**). This starts the Data Source Wizard. To access Help, click **Help** on the wizard pages, or open the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Help and look in [Data Source Wizard (DB2)](../core/data-source-wizard-db2-2.md).                                           |
   |     **DB2 Set Registers**      | The DB2 Set Registers property instructs the Adapter to execute one or more SQL SET statements. This optional property accepts a string value. The default value is an empty string, which denotes no statement. The supported syntax is a semi-colon delimited list of SET statement commands with a comma separate list of SET statement values “\<SET command 1> space \<SET value 1> semi-colon; \<SET command 2> space \<SET value a> comma \<SET value b> semi-colon”). For example, enter “SET CURRENT PATH 'DSN8910', 'HISDEMO'”. |
   | **Document Root Element Name** |                                                                                                                                                                                                                            The root element name that is used in the XML documents that are received from DB2.                                                                                                                                                                                                                            |
   | **Document Target Namespace**  |                                                                                                                                                                                                                            The target namespace that is used in the XML documents that are received from DB2.                                                                                                                                                                                                                             |
   |        **SQL Command**         |                                                                                                                                                                                                                        The select or stored procedure command that is executed one time for each polling interval.                                                                                                                                                                                                                        |
   |       **Update Command**       |                                                                                         The command that is executed after each row in the receive operation is processed. It can be either a delete statement that deletes the row from the table in the SQL command, or an update command that statically modifies one or more rows. When this option is specified, the SQL command must be a Select statement and must access a single table.                                                                                          |
   |            **URI**             |                                                                                                                                                                                                                                     A name identifying the receive port location. Default is DB2://.                                                                                                                                                                                                                                      |
   |      **Polling Interval**      |                                                                                                                                                                                                                                 The number of units between polling requests. Allowed range is 1 - 65535.                                                                                                                                                                                                                                 |
   |  **Polling Unit of Measure**   |                                                                                                                                                                                                                    The unit of measure (seconds, minutes, or hours) used between polling requests. Default is seconds.                                                                                                                                                                                                                    |


5. Select **OK** to save your changes.

6. For the **Receive Handler**,  select the host instance to run the adapter. The receive handler must be running on this host. Select the **Receive Pipeline**. 
   . Select **OK** to save your changes.

7. In the **Receive Locations**, right-click the receive location, and then **Enable**.  

## Create a DB2 adapter schema

1.  Open your BizTalk Visual Studio project.  

2.  Right-click the project, select **Add**, select **Add Generated Items**, and then select **Add**.  

3.  In the **Add Generated Items** dialog box, select **Add Adapter Metadata**.  

4.  In the Add Adapter Wizard, on the **Select Adapter** page, select **DB2**. In the Port list, select a configured send port or receive location, and then select **Next**.  

5. In the DB2 Adapter Schema Generation Wizard: 

    1. In **Database Information**, create a connection string, or select an existing connection string.  

    2. In **Schema Information**, define the default namespace, root elements, and port type to be used in the schema.  

        If you select **Receive port**, only a request document root element name is needed. If you select **Send port**, both request and response document root element names are required.  

    3. In **Statement Type Information**, select the type of database command to be issued.  

        If you selected receive ports on the previous page, you can choose either a SELECT SQL statement or a stored procedure. If you selected send ports on the previous page, you can choose to issue an updategram, stored procedure, or SELECT statement.  

    4. In **Statement Information**, enter the details about the DB2 database. Depending on the information you previously entered, the following properties are available:  

        1.  **Receive Select Statement** in the **Statement Information** dialog, type a SQL SELECT statement in the **SQL script** edit box. Optionally, click **Browse** to load a text file containing a statement.  

        2.  **Receive Stored Procedure** in the **Statement Information** dialog, click a **Stored procedure name**. In the Parameters list, click the **Value** checkbox for each parameter required.  

        3.  **Send Updategram** in the **Statement Information** dialog, click a **Table name**. In the **Parameters** list, click the **Value** checkbox for each column required. When using **BulkCopy**, you must click each **Value** checkbox to select all columns.  

        4.  **Send Stored Procedure** in the **Statement Information** dialog, click a **Stored procedure name**. In the **Parameters** list, click the **Value** checkbox for each parameter required.  

        5.  **Send Select Statement** in the statement Information dialog, type SQL SELECT statement in the SQL script edit box. Optionally, click **Browse** to load a text file containing a statement.  

6. Select **Finish** to complete the wizard. 

You now have a schema.