---
title: "How to Add a COM Component to an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [applications], COM components"
  - "managing [resources], COM components"
  - "applications, COM components"
  - "COM components, applications"
ms.assetid: fdda1a9d-96af-41fe-9d94-ee1fbd80a7c9
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a COM Component to an Application
This topic describes how to use the BizTalk Server Administration console or the command line to add a COM component to a BizTalk application:  
  
 When adding a COM component to an application, bear in mind the following important points:  
  
-   If you want to overwrite a COM component that already exists in the application, specify the Overwrite option. The overwrite option is required only when both artifacts have the same locally unique identifier (LUID). If not specified, and a COM component already exists in the application with the same LUID as the one being added, the add operation will fail. You can view the LUIDs for the artifacts in an application by using the [ListApp Command](../core/listapp-command.md).  
  
-   BizTalk Server does not check the dependencies for COM components to verify that they are present, so you should verify that any artifacts on which the component depends are present.  
  
-   If you add a 64-bit unmanaged COM or COM+ component, and you attempt to install the application that includes the COM or COM+ component on a 32-bit computer, the component will not be installed. It will install only on a 64-bit computer.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To add a COM component to an application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand BizTalk Server Administration, expand the BizTalk group, expand Applications, and then expand the application to which you want to add a COM component.  
  
3. Right-click the **Resources** folder, point to **Add**, and then click **Resources**.  
  
4. Click **Add**, select the COM component, and then click **Open**.  
  
5. In the **File type** drop-down list, click **System.BizTalk:Com**.  
  
6. In **Options**, select or clear the **Register the file at destination (regsvr32)** check box according to whether or not you want the component to be added to the Windows Registry when the application is installed.  
  
7. In **Destination**, type the full path of the location where the COM component is to be copied when the application is installed from the .msi file, including the file name. If this path is not provided, the file is not copied to the local file system during installation. This path is required if you selected the **Register the file at destination (regsvr32)** check box in the previous step.  
  
    Example: **%BTAD_InstallDir%\MyComponent.dll**  
  
8. When finished, click **OK**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:Com** [**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Options:Regsvr32OnInstall**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:Com /Overwrite /Source:"C:\Source Components\COM.dll" /Destination:"C:\New Components\COM.dll" /Options:Regsvr32OnInstall /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/ApplicationName**|Name of the BizTalk application to which to add the COM component. If the application name is not specified, the default BizTalk application for the group is used. If the name includes spaces, you must enclose it in double quotation marks (").|  
   |**/Type**|**System.BizTalk:Com** (This value is not case-sensitive.)|  
   |**/Overwrite**|Option to update an existing COM component. If not specified, and a COM component already exists in the application that has the same LUID as the COM component being added, the AddResource operation fails. You can view the LUIDs for the artifacts in an application by using the [ListApp Command](../core/listapp-command.md).|  
   |**/Source**|Full path of the COM component .dll file, including the file name. If the path includes spaces, you must enclose it in double quotation marks (").|  
   |**/Destination**|Full path of the location where the COM component .dll file is to be copied when the application is installed from the .msi file. If not provided, the file is not copied to the local file system during installation; therefore, the component cannot be added to the Windows registry during installation. If the path includes spaces, you must enclose it in double quotation marks ("). If you specify the Regsvr32OnInstallOption, you must also specify Destination.|  
   |**/Options**|**Regsvr32OnInstall.** Specify to add the COM component to the Windows registry when the application is installed from the .msi file. If you specify this option, you must also specify Destination.|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource Command: COM Component](../core/addresource-command-com-component.md)   
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)