---
title: "How to Export Bindings for a BizTalk Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bindings, exportings"
  - "applications, exporting"
  - "applications, bindings"
ms.assetid: 700d2781-480b-42ed-a313-1a67a7406369
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Export Bindings for a BizTalk Application
This topic describes how to use the BizTalk Server Administration console or the command line export the bindings for a BizTalk application to an .xml file. You can then import the binding file into another application, which overwrites the current bindings in the application with the imported bindings of the same name. For more information, see [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md). For more information about using binding files, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators or BizTalk Server Operators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To export bindings for a BizTalk application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and then expand **Applications**.  
  
3. Right-click the application whose bindings you want to export, point to **Export**, and then click **Bindings**.  
  
4. On the Export Bindings page, in **Export to file**, type the absolute path of the .xml file to which to export the bindings.  
  
    Example: **C:\Bindings\Application1Bindings_Staging1.xml**  
  
5. Ensure that **Export all bindings from the current application** is selected, and then click **OK**.  
  
6. To export all party information for the group, select the **Export Global Party information** check box.  
  
    The bindings are exported into an .xml file in the location that you specified.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask ExportBindings /Destination:** *value* [**/ApplicationName:**<em>value</em>] [**/GlobalParties**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask ExportBindings /Destination:"C:\Binding Files\MyBindings.xml" /ApplicationName:MyApplication /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/Destination**|Full path of the binding file to create, including the file name. If a binding file having the same path already exists, it is overwritten. If there are spaces in the path, you must enclose it in double quotation marks (").|  
   |**/ApplicationName**|Name of the application from which to export bindings. The application must exist. To verify the application name, you can use the **ListApps** command, as described in [ListApps Command](../core/listapps-command.md). If this parameter is not specified, the default BizTalk application is used. If there are spaces in the name, you must enclose it in double quotation marks (").|  
   |**/GlobalParties**|When specified, exports global party information for the group.|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Exporting Bindings](../core/exporting-bindings6.md)   
 [ExportBindings Command](../core/exportbindings-command.md)   
 [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md)