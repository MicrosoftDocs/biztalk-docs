---
title: "How to Create an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications, creating"
  - "creating, applications"
ms.assetid: 6a8682a7-3bef-4978-996f-5a9c5154ce62
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create an Application
There are three ways to create a new BizTalk application:  
  
- Create the BizTalk application by using the New Application command of the BizTalk Server Administration console or the AddApp command of the BTSTask command-line tool. You can find the procedures for doing this later in this topic.  
  
- Import an .msi file that was exported from another application. If the application does not already exist in the current BizTalk group, the application, including its artifacts, is automatically created in the current BizTalk group. For more information, see [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).  
  
- Deploy BizTalk assemblies from Visual Studio into a BizTalk application. If the application specified in Visual Studio does not already exist in the current BizTalk group, it is automatically created. For more information, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  
  
  Before creating a new application, you might want to decide how to configure the following options:  
  
- **What to name the new application.** Each application in the BizTalk group must have a unique name.  
  
- **Whether you need to add any references to other applications.** You must add a reference from this application to any applications containing artifacts that you want to reuse in this application. This creates a dependency between the applications, which affects the way that you must deploy them. For background information, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md) and [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).  
  
- **Whether you need to create more than one application.** You may need to deploy some artifacts into separate applications. For example, shared artifacts should be deployed into their own, separate application. For more information, see [Best Practices for Deploying a BizTalk Application](../core/best-practices-for-deploying-a-biztalk-application.md).  
  
  Once you have created an application, you can add artifacts to it and make other modifications, as described in the other topics in this section ([Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)).  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To create a BizTalk application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click the BizTalk group in which you want to create the new application, point to **New**, and then click **Application**.  
  
3. In **Name**, type the name of the application. The name must be unique in the BizTalk group.  
  
4. If you want to make this the default application for the BizTalk group, select the **Make this the default application** check box.  
  
5. In **Description**, type a description for the application.  
  
6. If this application will reuse artifacts from another application, click **References** and follow the remaining steps. Otherwise, click **OK** and take no further steps.  
  
7. Click **Add**, select the application that contains the artifacts you want to reuse in this application, and then click **OK**. Repeat this step for any additional applications for which you want to add references.  
  
8. If you want to remove an application from the list, select the application and click **Remove**.  
  
9. When finished, click **OK**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask AddApp /ApplicationName:** *value* [**/Default**] [**/Description:**<em>value</em>] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask AddApp /ApplicationName:MyApplication /Description:"My favorite application" /Server:MySQLServer /Database:BizTalkMgmtDb**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/ApplicationName**|Name of the application to be created. Names containing spaces must be enclosed in double quotation marks (").|  
   |**/Default**|When specified, makes the new application the default application for the BizTalk group.|  
   |**/Description**|Description of the application. Descriptions containing spaces must be enclosed in double quotation marks (").|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)   
 [AddApp Command](../core/addapp-command.md)