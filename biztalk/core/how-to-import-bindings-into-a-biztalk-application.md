---
title: "How to Import Bindings into a BizTalk Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bindings, applications"
  - "applications, importing"
  - "applications, bindings"
  - "bindings, importing"
ms.assetid: 89841b23-4e1b-46ff-8f00-cdad65d6216d
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Import Bindings into a BizTalk Application
This topic describes how to use the BizTalk Server Administration console or the command line to import bindings into a BizTalk application from an .xml file. You can also import bindings into a BizTalk group, as described in [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md).  
  
 You can import bindings that have been exported from an assembly, application, or group. If you import group bindings, only the bindings for an application having the same name are applied to the application into which you import the bindings. You can also import bindings from an application that has a different name. For instructions on exporting bindings, see [Exporting Bindings](../core/exporting-bindings6.md).  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To import bindings into a BizTalk application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and then expand Applications.  
  
3. Right-click the application into which you want to import bindings, point to **Import**, and then click **Bindings**.  
  
4. Click the binding file and click **Open**.  
  
    The artifacts in the binding file are written to the application. They display in appropriate folders of the application.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask ImportBindings /Source:** *value* [**/ApplicationName:**<em>value</em>] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    For example, the following command imports bindings into the application named MyApplication in the default BizTalk group.  
  
    **BTSTask ImportBindings /ApplicationName:MyApplication** /**Source:C:\Bindings\Binding1.xml**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/Source**|Full path of the binding file to import, including the file name. Paths that include spaces must be enclosed in quotation marks (").|  
   |**/ApplicationName**|Name of the BizTalk application into which the bindings are to be imported. The application must exist or the import operation will fail. If this parameter is not specified, the default BizTalk application is used. Application names that include spaces must be enclosed in quotation marks (").|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [ImportBindings Command](../core/importbindings-command.md)