---
title: "How to Remove a .NET Assembly, Certificate, or Other Resource Artifact from an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "virtual directories, deleting"
  - "managing [.NET assemblies], deleting"
  - "managing [applications], COM components"
  - "managing [applications], deleting artifcats"
  - "managing [certificates], deleting"
  - "deleting, binding files"
  - "binding files, deleting"
  - "managing, COM components"
  - "COM components, deleting"
  - "managing [artifacts], deleting"
  - ".NET assemblies, deleting"
  - "deleting, virtual directories"
  - "deleting, definitions [BAM]"
  - "applications, .NET assemblies"
  - "certificates, deleting"
  - "deleting, .NET assemblies"
  - "deleting, artifacts"
  - "deleting, certificates"
ms.assetid: b84eebac-261d-495f-80cd-ddda5bb08bef
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove a .NET Assembly, Certificate, or Other Resource Artifact from an Application
This topic describes how to use the BizTalk Server Administration console or the command line to remove the following resource artifacts from a BizTalk application. Using the procedures in this topic removes the artifact from the BizTalk Management database. It does not remove the artifact from the file system, certificate store, Internet Information Services (IIS), or the Windows registry, if it exists in any of these locations. In addition, if you remove a binding file, the bindings remain unchanged – only the binding file is removed.  
  
- .NET assemblies  
  
- COM components  
  
- Certificates  
  
- Ad hoc files  
  
- BAM definitions  
  
- Binding files  
  
- Virtual directories  
  
  If a virtual directory is explicitly added to an application, either by being imported from or added, it can be removed by using the procedures in this topic. If it was not explicitly added, but rather was added by reference when a receive location was configured, you cannot remove it by using the procedures in this topic. This is because the virtual directory is not stored in the BizTalk Management database. When you export the application .msi file the virtual directory will be obtained from IIS and added to the .msi file. When you import the .msi file, the virtual directory will be added to the BizTalk Management database for that group.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To remove a resource artifact from an application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand BizTalk Server Administration, expand the BizTalk group containing the resource artifact to remove, and then expand the application containing the artifact.  
  
3. Click the **Resources** folder, right-click the artifact, and then click **Remove**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask RemoveResource** [**/ApplicationName:**<em>value</em>] **/Luid:**<em>value</em> [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyAssembly, Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"**  
  
   |Parameter|Description|  
   |---------------|-----------------|  
   |**/ApplicationName**|Name of the BizTalk application containing the artifact to delete. If not specified, the default application is used. If the name includes spaces, you must enclose it in double quotation marks (").|  
   |**/Luid**|Locally unique identifier (LUID) of the artifact. You can obtain the LUID by using the **ListApp** command, as described in [ListApp Command](../core/listapp-command.md).|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [RemoveResource Command](../core/removeresource-command.md)