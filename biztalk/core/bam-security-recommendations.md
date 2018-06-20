---
title: "BAM Security Recommendations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, BAM"
  - "managing [BAM], security"
  - "BAM, security"
ms.assetid: 73613123-c1ed-477a-9f5c-342b2573c975
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BAM Security Recommendations
We recommend that you follow these guidelines for securing and deploying BAM in your environment:  
  
- If you are using [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)], the administration computer must have the following software installed to deploy BAM:  
  
  - [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]  
  
  - [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)] client tools  
  
  - [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)] Integration Services  
  
  - [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)] Analysis Services  
  
  - [!INCLUDE[SQLServer2005_SP3_long](../includes/sqlserver2005-sp3-long-md.md)], if you will be using BAM alerts  
  
    > [!NOTE]
    >  [!INCLUDE[SQLServer2005_SP3_short](../includes/sqlserver2005-sp3-short-md.md)] contains [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Services for [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)].  
  
  > [!NOTE]
  >  The user context under which the analysis DTS package runs must be a member of the db_owner [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] role of the BAM Primary Import and BAM Star Schema databases. In addition, the service account under which Analysis Services runs must be an OLAP administrator and must be a db_owner of the BAM Star Schema database. For more information, see the Microsoft Help and Support Web site at [http://go.microsoft.com/fwlink/?LinkId=22781](http://go.microsoft.com/fwlink/?LinkId=22781).  
  
- Multiple users need access to the live and archived data: salespeople, business managers, and others. These users must have domain accounts in the domain where the BAM Primary Import and BAM Analysis databases are (corporate domain), but their accounts do not need to have access to BizTalk resources.  
  
- For users to access views of the BAM data, you must use the BAM management utility (BM.exe) to grant the users permissions to the views, and the users must have SQL logins. For more information about the BAM management utility, see [BAM Management Utility](../core/bam-management-utility.md).  
  
- To add users to roles that have access to the cubes in the BAM Analysis database, you must have an administration computer in the same domain as the BAM databases.  
  
- The person administering BAM must be db_owner for the BAM Primary Import, Star Schema, and BAM Archive databases. That person must also be an OLAP administrator for the BAM Analysis database.  
  
- If you are deploying Microsoft Office Excel workbooks (.xls files), Excel must be installed on the administration computer. Before you deploy a workbook, open it and ensure that the macro security is set to high, and that there are no warnings.  
  
- If there is no business need to distribute to the users BAM Excel workbooks that connect to the real data, we recommend that you deploy the workbooks by using XML files. This eliminates the need to install Excel on the administration computer, and the need to verify the macro security level.  
  
  > [!IMPORTANT]
  >  When you remove a user's permissions on a view, you must also remember to eliminate any subscriptions to alerts that the user has set. For more information about removing subscribers from an alert, see [How to Remove Subscribers from an Alert](../core/how-to-remove-subscribers-from-an-alert.md).  
  
## See Also  
 [Minimum Security User Rights](../core/minimum-security-user-rights.md)   
 [Security Recommendations for a BizTalk Server Deployment](../core/security-recommendations-for-a-biztalk-server-deployment.md)