---
title: "How to Export Bindings for a BizTalk Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bindings, exporting"
  - "groups, bindings"
  - "groups, exporting"
ms.assetid: 51955266-f87f-41c9-992c-93036b40f663
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Export Bindings for a BizTalk Group
This topic describes how to use the BizTalk Server Administration console or the command line to export the bindings for a BizTalk group to an .xml file. You can then import these bindings into a BizTalk group or application, as described in [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md) and [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md). For more information about using binding files, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).  
  
> [!NOTE]
>  Exporting bindings for a group always exports global party information, whether this option is specified or not.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators or BizTalk Operators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To export bindings for a BizTalk group  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, right-click **Applications**, point to **Export**, and then click **Bindings**.  
  
3. On the Export Bindings page, in **Export to file**, type the absolute path of the .xml file to which to export the bindings.  
  
    Example: C:\Bindings\Group1Bindings_Staging1.xml  
  
4. Ensure that **Export all bindings from the current group** is selected, and then click **OK**.  
  
    The bindings are exported to an .xml file in the location that you specified.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask ExportBindings /Destination:** *value* **/GroupLevel** [**/GlobalParties**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask ExportBindings /Destination:"C:\Binding Files\MyBindings.xml" /GroupLevel /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/Destination**|Full path of the binding file to create, including the file name. If a binding file having the same path already exists, it is overwritten. If there are spaces in the path, you must enclose it in double quotation marks (").|  
   |**/GroupLevel**|When specified, all bindings in the current BizTalk group are exported.|  
   |**/GlobalParties**|When specified, exports global party information for the group.|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Exporting Bindings](../core/exporting-bindings6.md)   
 [ExportBindings Command](../core/exportbindings-command.md)   
 [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md)