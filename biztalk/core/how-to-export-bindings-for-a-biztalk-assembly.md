---
title: "How to Export Bindings for a BizTalk Assembly | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblies, bindings"
  - "assemblies, exporting"
  - "exporting, assemblies"
ms.assetid: 7e37348d-5fa5-43cc-b3c0-2d8cb6a8f394
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Export Bindings for a BizTalk Assembly
This topic describes how to use the BizTalk Server Administration console or the command line to export the bindings for a BizTalk assembly to an .xml file. You can then import these bindings into a BizTalk application, which overwrites existing bindings with the imported bindings of the same name. You might want to export the bindings for an assembly before you update it, so that you can import the bindings after you update it to reapply them. For more information about updating applications and assemblies, see [Updating BizTalk Applications](../core/updating-biztalk-applications.md). For more information about using binding files, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators or BizTalk Server Operators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To export bindings for a BizTalk assembly  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and then expand Applications.  
  
3. Right-click the application containing the assembly, point to **Export**, and then click **Bindings**.  
  
4. On the Export Bindings page, in **Export to file**, type the absolute path of the .xml file to which to export the bindings.  
  
    Example: **C:\Bindings\MyAssemblyBindings_Staging1.xml**  
  
5. On the Export Bindings page, click **Export bindings for the selected assembly**, and then in **Assembly**, click the assembly.  
  
6. If you want to export all of the party information in the group, select **Export Global Party Information**.  
  
    The bindings are exported to an .xml file in the location that you specified.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask ExportBindings /Destination:** *value* **/AssemblyName:** *value* [**/GlobalParties**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask ExportBindings /Destination:"C:\Binding Files\MyBindings.xml" /AssemblyName:"ErrorHandling.ErrorHandler, Version=1.0.0.0, Culture=neutral, PublicKeyToken=11e921d58826420e" /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/Destination**|Full path of the binding file to create, including the file name. If a binding file having the same path already exists, it is overwritten. If there are spaces in the path, you must enclose it in double quotation marks (").|  
   |**/AssemblyName**|Locally unique identifier (LUID) of the assembly from which to export bindings. You can obtain a list of LUIDs for the artifacts in an application by using the [ListApp Command](../core/listapp-command.md).|  
   |**/GlobalParties**|When specified, exports global pary information for the group.|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Exporting Bindings](../core/exporting-bindings6.md)   
 [ExportBindings Command](../core/exportbindings-command.md)   
 [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md)