---
title: "How to Add a Pre- or Post-processing Script to an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [applications], adding scripts"
  - "managing [scripts], applications"
  - "applications, scripts"
  - "managing [scripts], adding"
  - "scripts, adding to applications"
  - "scripts"
ms.assetid: 729cb236-b9cf-468a-8b98-a24d86e60d3c
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a Pre- or Post-processing Script to an Application
This topic describes how to use the BizTalk Server Administration console or the command line to add a pre- or post-processing script to an application. When you add a script to an application, the script is included in the application .msi file, and runs when the application is imported, installed, or uninstalled.  
  
 When you add a script, you must specify whether it is a pre-preprocessing script, which will run before application import or installation starts, or a post-processing script, which will run after application import or installation completes. Pre- and post-processing scripts also run at uninstallation, in the opposite order to that in which they ran at installation: pre-processing scripts run after uninstallation and post-processing scripts run before uninstallation.  
  
 You can also remove a script from an application. For instructions, see [How to Remove a Pre- or Post-processing Script from an Application](../core/how-to-remove-a-pre-or-post-processing-script-from-an-application.md).  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To add a script to an application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. Expand the BizTalk group, expand Applications, and then right-click the folder of the application to which you want to add a script.  
  
3. Point to **Add**, and do one of the following:  
  
   -   Click **Pre-processing Scripts** if you want the script to run before application import or installation begins or after uninstallation.  
  
   -   Click **Post-processing Scripts** if you want the script to run after application import or installation, or before uninstallation.  
  
4. Click **Add** and browse to the script file to add.  
  
5. Select the script file and click **Open**.  
  
6. If you want to overwrite a script file that already exists in the application, select the **Overwrite all** check box. The script file must have the same file name as the one being added to be overwritten. Otherwise the new script will be added, and the existing script will remain in the application unchanged.  
  
7. Click the **File type** drop-down list and click the file type – either **System.BizTalk:PreprocessingScript** or **System.BizTalk:PostprocessingScript**.  
  
8. If necessary, in **Destination location** type the path where you want the script file to be copied when the application is installed, and then click **OK**. The default path will install the script to the application installation folder (%BTAD_InstallDir%).  
  
> [!NOTE]
>  If you do not provide this path, the script will not be copied to the local file system on installation. If the script should run when the application is uninstalled, be sure to provide this path; otherwise the script will not be present on the local file system and will not run during uninstallation.  
  
 The script is added to the application and is displayed in the Resources folder of the application.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:PreProcessingScript**&#124;**System.BizTalk:PostProcessingScript** [**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>][**/Property:Args="**<em>argument list</em>**"**]  
  
    Example:  
  
    **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:PreProcessingScript /Overwrite /Source:"C:\Source Scripts\MyScript.vbs" /Destination:"C:\New Scripts\MyScript.vbs" /Server:MyDatabaseServer /Database:BizTalkMgmtDb /Property:Args="argument1 argument2"**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/ApplicationName**|Name of the BizTalk application to which to add the script. If the application name is not specified, the default BizTalk application is used. If the name includes spaces, you must enclose it in double quotation marks (").|  
   |**/Type**|**System.BizTalk:PreProcessingScript** or **System.BizTalk:PostProcessingScript**, depending on the type of script to add. Use **System.BizTalk:PreProcessingScript** if you want the script to run before application import or installation or after uninstallation. Use **System.BizTalk:PostProcessingScript** if you want the script to run after application import or installation, or before uninstallation.|  
   |**/Overwrite**|Update an existing script. If not specified, and a script file already exists in the application that has the same name as the script file being added, the add operation will fail.|  
   |**/Source**|Full path of the script file, including the file name. If the path includes spaces, you must enclose it in double quotation marks (").|  
   |**/Destination**|Full path of the location where the script file is to be copied when the application is installed from the MSI file. If not provided, the file is not copied to the local file system during installation. If the path includes spaces, you must enclose it in double quotation marks (").|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
   |**/Property:Args=**|Zero or more arguments. The arguments provided here will be passed into the script when it is invoked.|  
  
## See Also  
 [Managing Pre- and Post-processing Scripts](../core/managing-pre-and-post-processing-scripts.md)   
 [AddResource Command: Preprocessing Script](../core/addresource-command-preprocessing-script.md)   
 [AddResource Command: Postprocessing Script](../core/addresource-command-postprocessing-script.md)