---
title: "Planning for the BAM Portal | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BAM portal, security"
  - "BAM portal, prerequisites"
  - "BAM portal, deploying"
  - "developing, BAM portal"
  - "planning, BAM portal"
  - "BAM portal, planning"
  - "BAM portal, developing"
  - "deploying, BAM portal"
  - "security, BAM portal"
ms.assetid: 8a8bd331-c5a8-4d8b-9e93-96e6cd581a1d
caps.latest.revision: 36
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for the BAM Portal
This topic describes items that you should consider when planning your Business Activity Monitoring (BAM) portal deployment.  
  
## Prerequisites  
 **System requirements**. In addition to the system requirements for BizTalk Server, you must install the following software in order to install the BAM portal:  
  
-   Internet Information Services (IIS)  
  
-   Microsoft Office Excel  
  
-   Microsoft Internet Explorer  
  
-   Microsoft .NET Framework  
  
-   Microsoft XML Core Services (MSXML) 6.0  
  
-   Microsoft Data Access Components (MDAC) 2.7  
  
## Configuration planning  
 **Migrating from previous versions of BizTalk Server**. After migrating from previous versions of BizTalk Server, your installations of the existing pages in the BAM portal might no longer be functional. For the BAM portal to successfully function, refer to the considerations and guidelines for BAM provided in the BizTalk Server Upgrade Guide.  
  
 **Databases**. Consider the following information when planning for databases:  
  
- You will need to plan for indexes of your databases to enhance performance. Date and time columns generally require an index on the progress dimension. Queries on progress dimensions with no indexes are slow and will negatively impact performance on the BAM Primary Import table.  
  
- You will need to consider whether you should set up BAM without alerts.  
  
  **SQL Server Notification Services**. SQL Server Notification Services does not support local host or IP addresses for server names to identify servers.  You may encounter this in two locations:  
  
1. During configuration - If you selected BAM and turned on alerts, the configuration process will ask for a server name.  
  
2. Modifying the configuration .xml file - If you attempt to modify the configuration .xml file left over from the configuration process in order to reuse it.  
  
   **IIS installation**. BAM Portal only runs on a 32-bit mode. If you are installing IIS on a 64-bit machine then you must ensure that ASP.NET 2.0 is enabled on 32-bit mode. To do this, open IIS Manager, open **Application Pool**, select the application pool (BAMAppPool), and then click **Advanced Settings**. In **Enable 32-bit applications**, select **True**. For more information, see BizTalk Server Upgrade Guide.  
  
## Deployment planning  
 **Multicomputer deployment**. Is your deployment of BizTalk Server across a multicomputer environment? If your BAM portal is configured on a different server than your alerts database, you must increase the query service timeout value in a multiserver environment. For additional configuration information, see [Customizing the BAM Portal Configuration](../core/customizing-the-bam-portal-configuration.md).  
  
- **Multiculture deployment**. Is your deployment of BizTalk Server across a multiculture environment? When you install BizTalk Server the user interface (UI) is in the language of the version that you installed and the BAM portal acquires the culture settings of the user who configures it. To modify the BAM portal web.config file to reflect the proper culture setting, see [Customizing the BAM Portal Configuration](../core/customizing-the-bam-portal-configuration.md).  
  
  **Cluster deployment**. Are you deploying in a network load balancing (NLB) cluster? See [Customizing the BAM Portal Configuration](../core/customizing-the-bam-portal-configuration.md) for additional configuration information.  
  
  **SSL**. Are you deploying the BAM portal on an IIS installation using SSL? See the [Customizing the BAM Portal Configuration](../core/customizing-the-bam-portal-configuration.md) topic for additional configuration information.  
  
  Users who are creating views must have the BAM Add-In for Excel installed.  
  
## Permissions  
 **BAM Manager**. The add-account command of the BAM Manager (bm.exe) does not automatically grant database permissions to the user added. This is due to the fact that to run the BAM Manager you only need dbo permissions. As a result, accessing real-time aggregations (RTAs) from the BAM portal causes SQL Server to fail unless you belong to certain groups within SQL Server, as described next.  
  
 **SQL Server roles**. To grant a user access to a database, you must be a member of the securityadmin or sysadmin group.  
  
 A member of the securityadmin or sysadmin group can grant permissions by running sp_grantdbaccess and sp_grantlogin.  
  
 For more information about roles in SQL Server, see "Roles in the SQL Server Architecture" at [http://go.microsoft.com/fwlink/?LinkId=56205](http://go.microsoft.com/fwlink/?LinkId=56205).  
  
## Development planning  
 **Connection strings for PivotTables**. The BAM Manager utility does not always change the connection strings for real-time aggregation (RTA) PivotTable definitions during deployment. This occurs when the RTA PivotTable has preexisting OLAP connection strings that have been manually edited and the casing of the value key is incorrect. For example, in this line from the BAM definition XML file the key is RTARef rather than the expected RtaRef:  
  
 **\<PivotTableView CubeRef="POCube" RTARef="POAmountByLocation"\>**  
  
 This causes the PivotTable to be generated through the OLAP cube rather than through the RTA PivotTable.  
  
 **Field names**. We recommend that you choose distinct naming conventions for field names when developing a monitoring solution. BAM does not require unique names between the view section of the BAM definition and the OLAP cube of the aggregation.  As a result, the column chooser and the field selection drop-down list in the Activity Search query builder can contain two fields with the same names. This can cause errors when trying to select the correct fields to include in the results.  
  
 For BizTalk Server ports that use pass-through pipelines, it is not possible to track data from the message payload. Pass-through pipelines do not evaluate the message types into the schema names, which results in all the messages having null schemas.  
  
- Since the tracking profile is mapped to a port and schema pair, attempting to track message payload data for a pass-through pipeline results in nothing being tracked.  
  
  **Names for PivotTables**: When planning for and developing the user experience in the aggregations task of the BAM portal, you should create user friendly names for the PivotTables that you create in Excel.  You can customize the name by right-clicking on a PivotTable and selecting Table options from the context menu.  
  
  **Date ranges**. When creating queries and instance alerts using the Activity Search page keep in mind that if the @@DateFirst value in your SQL queries does not match the CultureInfo.CurrentCulture.DateTimeFormat.FirstDayOfWeek value, then the date ranges shown on the search page will not match the week boundaries used to generate the aggregations.  
  
  For example, if the week start day in SQL Server is set to Sunday, then the date range for the second week of 2005 is from 1/2/2005 through 1/8/2005 and aggregations in SQL Server and OLAP shown for week 2 are based on this date range. However, if the BAM portal specifies a week start date of Saturday, then a user performing drill down on week 2, 2005 will see a date range of from 1/8/2005 through 1/14/2005 on the search page. As a result, the value returned by the search query may not match the aggregate value shown in the PivotTable.  
  
  To obtain the desired result adjust the time range in the query to retrieve the desired date range.  
  
  **Distributed navigation**. The BAM portal distributed navigation feature allows users to see activity relationships across remote boundaries. When developing activities consider the following:  
  
- There may be situations in which you will place related activities from separate BAM Primary Import databases into the same view. It is possible that the activities could have the same names but exist on separate servers, such as two different departments, that both have a Purchase Order activity. When the BAM portal user selects View in the My View pane on the portal they will see both activities listed under each task.  
  
- If users are using BAM portals on different servers to view the deployed views, references need to be enabled symmetrically in order for two portal experiences, each running against its local BAM Primary Import database, to be the same.  
  
## See Also  
 [Customizing the BAM Portal Configuration](../core/customizing-the-bam-portal-configuration.md)