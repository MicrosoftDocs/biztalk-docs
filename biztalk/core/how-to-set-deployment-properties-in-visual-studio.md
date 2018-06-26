---
title: "How to Set Deployment Properties in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2c6752e-c50d-4dd0-ac07-bf36ca10559c
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Set Deployment Properties in Visual Studio
Before you can deploy a solution from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] into a BizTalk application, you must first set project properties. If a solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] contains multiple projects, you must separately configure properties for each project.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that has Read/Write permission on the local file system. The Administrators account on the local computer has this permission.  
  
### To enable project deployment in Configuration Manager  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] click **Build** on the main menu, then click **Configuration Manager**.  
  
2. Check the **Deploy** option for each project that needs to be deployed from the opened solution.  
  
### To configure project properties  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer right-click a project for which you want to configure properties, and then click **Properties**.  
  
2. Click the **Deployment** tab in Project Designer.  
  
3. Configure project properties as described in the following table, and then click **OK**.  
  
4. Repeat steps 1, 2, and 3 for each project in the solution.  
  
   |Property|Value|Explanation|  
   |--------------|-----------|-----------------|  
   |Application Name|\<Name\>|Name of the BizTalk application to which to deploy the assemblies in this project. If the application already exists, the assemblies will be added to it when you deploy the project. If the application does not exist, the application will be created. If this field is blank, the assemblies will be deployed to the default BizTalk application in the current group. Names that include spaces must be enclosed by double quotation marks (").|  
   |Configuration Database|\<BizTalk Management database name\>|Name of the BizTalk Management database for the group, BizTalkMgmtDb by default.|  
   |Server|\<Server name\>|Name of the SQL Server instance that hosts the BizTalk Management database on the local computer. In a single-computer installation, this is usually the name of the local computer. **Note:**  If you move this BizTalk project to a different computer, you probably will need to modify the Server property to reflect the new computer name before you will be able to deploy the assembly.|  
   |Redeploy|True or False|Setting this to True (the default) enables you to redeploy the BizTalk assemblies without changing the version number.|  
   |Install to Global Assembly Cache|True or False|Setting this to True (the default) installs the assemblies to the Global Assembly Cache (GAC) on the local computer when you install the application. Set this to False only if you plan to use other tools for this installation, such as gacutil.|  
   |Restart Host Instances|True or False|Setting this to True automatically restarts all host instances running on the local computer when the assembly is redeployed. If set to False (the default), you must manually restart the host instances when you redeploy an assembly. **Note:**  If you are redeploying assemblies from the solution level, host instances will be restarted once for each project that has this option set to True. This may result in multiple restarts. If you plan to redeploy from the solution level, you may want to set this property to True on only one project in the solution to avoid multiple host instance restarts. This should be set on the last project that will be redeployed in the solution. In addition, if a host instance is stopped when you perform the redeploy, it will not be started.|  
   |Enable Unit Testing|True or False|Specifies whether to enable unit testing for the project.|  
  
## See Also  
 [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)