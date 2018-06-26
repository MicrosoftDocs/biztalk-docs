---
title: "BizTalk Adapter for Host Files Configuration | Microsoft Docs"
description: Create the metadata assembly, send port, receive port and location, schema, and application to use the BizTalk Adapter for Host Files in Host Integration Server (HIS)
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e346515-129b-4170-80ba-9b9628dd5359
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# BizTalk Adapter for Host Files Configuration

## Overview
The BizTalk Adapter for Host Files is a send and receive adapter that enables BizTalk orchestrations to interact with host systems. Specifically, the adapter enables send and receive operations over TCP/IP and APPC connections to host files that run on mainframe and AS/400 platforms. Based on Host Integration Server technology, the adapter uses Data Access Library metadata assemblies to configure connections, and the Microsoft .NET Framework data provider for host files to issue SQL commands and stored procedures.  

 The adapter serves two main functions:  

- For **Send** operations (both One Way and Solicit Response), the adapter sends SQL commands and system commands to a host file instance, with the option of soliciting a response.  

- For **Receive** operations (One Way only) the adapter creates an SQL command that polls host file objects and creates per-row messages, which are then submitted to the BizTalk message system.  

  In addition, the BizTalk Adapter for Host Files uses the standard BizTalk Adapter tracing tool as a troubleshooting mechanism.  

> [!NOTE]
>  The BizTalk Adapter for Host Files is a non-transactional adapter. This means that once an action is performed, it cannot be undone or rolled back.  

## Create a metadata assembly
After you install the adapter, you can create a metadata assembly that describes your remote system to BizTalk Server.

Part of the process of creating a Host File application in Visual Studio is describing the layout of the host file system. This process creates both a metadata assembly and a schema. The metadata assembly is a programmatic representation of the remote host file system, whereas the schema is an XML representation of the host file system. You will use the metadata assembly to describe the host file system to BizTalk Server.  

For more information about how to create a Host File application in Visual Studio, see [Creating an Application with the Managed Data Provider for Host Files](./creating-an-application-with-the-managed-data-provider-for-host-files2.md).  

## Create a send port
Sign in with an account that is a member of the BizTalk Server Administrators group.

1. In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then select your application.  

2. Right-click **Send Ports**, select **New**, and then select **Static One-way Send Port** or **Solicit Response Send Port**.  

3. In the **Send Port Properties**, set the **Transport Type** to **Host File**. Select **Configure**, and enter the following properties:  


   |            Use this            |                                                                                                                                                                                                                           To do this                                                                                                                                                                                                                            |
   |--------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |     **Connection String**      | The name of a connection string that is used to connect to the Host File database.<br /><br /> To configure a new or existing connection string, click the ellipsis (**…**). This starts the Data Source Wizard. To access Help, click **Help** on the wizard pages, or open the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Help and look in [Data Source Wizard (Host Files)](../core/data-source-wizard-host-files-2.md). |
   | **Document Target Namespace**  |                                                                                                                                                                                        The target namespace that is used in the XML documents that are sent to the host.                                                                                                                                                                                        |
   | **Response Root Element Name** |                                                                                                                                                            The root element name that is used in the XML documents that are received from the host. (This property may be empty for a one-way port.)                                                                                                                                                            |
   |            **URI**             |                                                                                                                                                                                             Uniform resource identifier. A name to identify the send port location.                                                                                                                                                                                             |


4. Select **OK** to save your changes.

5. For the **Send Handler**, select the host instance to run the adapter, and select the **Send Pipeline**. 

6. Select **OK** to save your changes.

7. In the **Send Ports**, right-click your new send port, and select **Enlist** and then **Start**.  

## Create a receive port and location
Sign with an account that is a member of the BizTalk Server Administrators group. 

1. In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then select your application.  

2. Right-click **Receive Ports**, select **New**, and then select **Static One-way Receive Port**. Configure your **Receive Port Properties**, and select **OK** to save your changes.  

3. Right-click **Receive Locations**, select **New**, and then select **One-way Receive Location**. Select the receive port you created, and then **OK**.  

4. In the **Receive Location Properties**, set the **Transport Type** to **HostFiles**. Select **Configure**, and enter the following properties:  


   |            Use this            |                                                                                                                                                                                                                                                                                                                                                                                                                                                           To do this                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   |--------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |     **Connection String**      | Enter the name of a connection string that will be used to connect to the host database.<br /><br /> To configure a new or existing connection string, click the ellipsis (**…**). This starts the Data Source Wizard. To access Help, click **Help** on the wizard screens, or open the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Help and look in [Data Source Wizard (Host Files)](../core/data-source-wizard-host-files-2.md).<br /><br /> When configuring a receive location or send port based on the BizTalk Adapter for Host Files, the metadata definition should be created as a Host Integration Designer XML (HIDX) metadata file for encoding and decoding records. For instructions on how to create a HIDX file, see [Creating an Application with the Managed Data Provider for Host Files](./creating-an-application-with-the-managed-data-provider-for-host-files2.md). |
   | **Document Root Element Name** |                                                                                                                                                                                                                                                                                                                                                                                                                    The root element name that is used in the XML documents that are received from the host.                                                                                                                                                                                                                                                                                                                                                                                                                     |
   | **Document Target Namespace**  |                                                                                                                                                                                                                                                                                                                                                                                                                     The target namespace that is used in the XML documents that are received from the host.                                                                                                                                                                                                                                                                                                                                                                                                                     |
   |        **SQL Command**         |                                                                                                                                                                                                                                                                                                                                                                                                                             The Select command that is executed one time for each polling interval.                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |       **Update Command**       |                                                                                        The command that is executed after each row in the receive operation is processed. It can be either a delete statement that deletes the row from the table in the SQL command, or an update command that statically modifies one or more rows. When this option is specified, the SQL command must be a Select statement and access a single table.<br /><br /> You can specify additional properties by clicking the ellipsis (**…**) button. This opens the **Change Command** dialog box, which provides three options:<br /><br /> -   **Do nothing** clears the other two options if selected.<br />-   **Delete after read** deletes the row after the adapter has read it.<br />-   **Update** lets you type an SQL command to be updated.                                                                                        |
   |            **URI**             |                                                                                                                                                                                                                                                                                                                                                                                                                           Uniform resource identifier. A name identifying the receive port location.                                                                                                                                                                                                                                                                                                                                                                                                                            |
   |      **Polling Interval**      |                                                                                                                                                                                                                                                                                                                                                                                                                            The number of units between polling requests. Allowed range is 1 - 65535.                                                                                                                                                                                                                                                                                                                                                                                                                            |
   |  **Polling Unit of Measure**   |                                                                                                                                                                                                                                                                                                                                                                                                               The unit of measure (seconds, minutes, or hours) used between polling requests. Default is seconds.                                                                                                                                                                                                                                                                                                                                                                                                               |


5. Select **OK** to save your changes.  

6. For the **Receive Handler**, select the host instance. The receive handler must be running on this host. Select your **Receive Pipeline**.

7. Select **OK** to save your changes.  

8. In the **Receive Locations**, right-click the receive location, and select **Enable**.  

## Create a Schema
Use the Host File Schema Generation Wizard to create the XSD schemas for the BizTalk Adapter for Host Files. After you create the schema, you are ready to continue configuration on the BizTalk Server side.  

1. Open your BizTalk Server Visual Studio project.  

2. Right-click the project, select **Add**, select **Add Generated Items**, and then select **Add Adapter Metadata**.  

3. In the Add Adapter Wizard, on the **Select Adapter** page, select **Host File**, and then select **Next**.  

4. In the Host File Adapter Schema Generation Wizard:

   1. In **Database Information**, browse to an existing connection string or create a new one.  

       This can be Initial Catalog, Package Collection, (TCP Address and Port) or (APPC Local LU, Remote LU, and Mode), (User Name and Password), or (Integrated Security). Maximum length is 1024.  

   2. In **Schema Information**, define the default namespace, root elements, and port type that you want to use in the schema.  

       If you select **Receive port**, only a request document root element name is needed. If you select **Send port**, request and response document root element names are required.  

   3. In **Statement Type Information**, select the type of database command to be issued.  

       If you selected send ports on the previous page, you can choose to issue an updategram, stored procedure, or SELECT statement. If you selected receive ports, this step is unnecessary.  

   4. In **Statement Information**, enter the details about the host file. Depending on the information you previously entered on earlier pages, enter the following properties. If you selected send port:  

       -   **Send Updategram** If you chose to use a send port and updategrams, you can select the updategram operation here, and also the table and columns that will be present in the updategram.  

       -   **Send System Command** If you chose to use a send port and issue a stored procedure, you can select a stored procedure from the current connection’s catalog. You do not have to enter values for all parameters on this page.  

       -   **Send Select Statement** If you chose to use a send port with an SQL Select statement, you can either select or browse to the statement here.  

      If you selected receive port:  

       -   **Receive Select Statement** If you chose to use a receive port with an SQL statement, you can either select or browse to the statement here.  

       -   **Send Updategram** If you chose to use a send port and updategrams, you can select the updategram operation here, and also the table and columns that will be present in the updategram.  

       -   **Send Stored Procedure** If you chose to use a send port and issue a stored procedure, you can select a stored procedure from the current connection’s catalog. You do not have to enter values for all parameters on this page.  

       -   **Send Select Statement** If you chose to use a send port with an SQL Select statement, you can either select or browse to the statement here.  

5. Select **Finish** when complete.

## Create a BizTalk Application
After you create the schema, you can code your BizTalk application. Your application uses the metadata assembly that you created in Visual Studio, in addition to the schema and ports that you created..  

1.  Create a BizTalk project in Visual Studio. 

2.  Use the schema that you created to describe the Host File system to the BizTalk application.  

3.  Use the send port that you created to send data to the host file system.  

4.  If necessary, use the receive port and location that you created.  

5.  Add any additional orchestrations, components, or code, as necessary.  

6.  Test your application.  

7.  After you finish testing your application, create an .msi package to move your application to a staging or live server. When you are creating a BizTalk Server .msi package, be sure to include the host file metadata assembly you created.

## See Also  
 [Managed Data Provider for Host Files](./managed-data-provider-for-host-files2.md)