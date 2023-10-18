---
description: "Learn more about: Project Designer: Deployment Tab"
title: "Project Designer: Deployment Tab"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Project Designer: Deployment Tab
The **Deployment** property tab of the Project Designer allows you to configure the deployment attributes for the BizTalk project. You must configure both the **Server** and the **Configuration Database** (also known as the BizTalk Management database) properties as a set for deployment to be successful.  
  
## Application Name  
 Specify the BizTalk application in which to deploy the assembly. If this is empty, the project will be deployed into the default application.  
  
## Configuration Database  
 You use this field to specify the name of the BizTalk Configuration database for the deployed assembly. This applies if you have configured the BizTalk project as a deployment project.  
  
> [!NOTE]
>  The BizTalk Configuration database is also referred to as the BizTalk Management database.  
  
 The default Configuration database name is BizTalkMgmtDb.  
  
## Server  
 This is the name of the server where the Configuration repository (also known as the BizTalk Management or Configuration database) is located. You deploy the BizTalk project to this server if you configure the BizTalk project as "Deployment."  
  
## Redeploy  
 You use the **Redeploy** property to determine whether to delete the existing configuration and re-create the configuration each time you deploy the assembly. The default value is `True`.  
  
## Install to Global Assembly Cache  
 You use the **Install to Global Assembly Cache** property to indicate if [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] needs to install the BizTalk assembly to the global assembly cache (GAC).  
  
## Restart Host Instances  
 If you set **Restart Host Instances** to **True**, the host instances on the local computer will be restarted when the project is deployed by [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. This is useful during the development cycle when you are making changes and frequently redeploying; you will not have to manually restart related host instances.  
  
 If you do not restart related host instances, your latest changes may not be reflected in your BizTalk application because the old version may still be cached. Restarting the host instance purges cached assemblies.  
  
## Enable Unit Testing  
 Specified whether to enable unit testing for the project.  
  
## See Also  
 [How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)   
 [BizTalk Project Properties Window](../core/biztalk-project-properties-window.md)
