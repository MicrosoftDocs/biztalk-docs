---
description: "Learn more about: Production Tasks for BizTalk Application Deployment"
title: "Production Tasks for BizTalk Application Deployment"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Production Tasks for BizTalk Application Deployment
The following are the steps involved in deploying a BizTalk application to your production environment.  
  
> [!IMPORTANT]
>  You should never deploy assemblies from Visual Studio on a production computer. To enable the redeployment, Visual Studio may undeploy, unbind, stop, and unenlist assemblies that exist in the same or different applications. Although this is necessary and appropriate in the development environment, it can cause unexpected and undesired consequences in a production environment. In addition, to avoid the possibility of anyone's attempting to deploy an assembly from Visual Studio on a production computer, we recommend that you not install Visual Studio on a production computer.  
  
> [!IMPORTANT]
>  Be careful when updating applications on which other applications depend in a production environment, so that you do not disrupt other running applications. For more information, see [Important Considerations for Updating Applications](../core/important-considerations-for-updating-applications.md).  
  
1.  **Copy the .msi file to your production environment.** As described in [Testing Tasks for BizTalk Application Deployment](../core/testing-tasks-for-biztalk-application-deployment.md), when the BizTalk application has completed staging and is ready for production, the IT administrator responsible for staging configuration provides an .msi file to use for production deployment. You can copy this .msi file onto your production computers, and then, as described in the next step, import the BizTalk application from the .msi file into BizTalk Server. You also use the .msi file to install the application onto the computers that are to run the application. A complete BizTalk solution can consist of one or more applications, so you may receive several .msi files to deploy.  
  
2.  **Import the application from the .msi file.** You can use the Import Wizard, available from the BizTalk Server Administration console, to import the contents of the .msi file into an application on the current instance of BizTalk Server. For more information, see [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md). If the specified application does not already exist, importing the .msi file creates it. You can then view the application and modify its configuration and contents from the administration console. You might need to do this, for example, to configure certificates and endpoints, such as URLs as well as modify the bindings for your production environment. For more information, see [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md). If a binding file was added to the application that has the appropriate bindings for the production environment, you can apply the bindings during the import process. For more information, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).  
  
3.  **Install and start the application.** You can now install the application on all of the computers that will run the application and start the application in the administration console. You can install the application by double-clicking the .msi file. For more information, see [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md).  
  
4.  **Export binding files and add them back into the application (optional).** To make it easier to import the application back into the production environment at a later time to deploy changes or additions, you may want to export the application bindings and then add them back into the application, specifying a Production target environment for the bindings. When you later import the application .msi file back into BizTalk Server in the production environment, you can specify that these bindings be applied. For more information, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).  
  
5.  **Export the application to a new .msi file (optional).** If you made configuration changes or additions to the application, and want the changes to be reflected in the .msi file (for example to deploy the application to other BizTalk groups), you can export a new .msi file, as described in  [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).  
  
## See Also  
 [Application Deployment Tasks](../core/application-deployment-tasks.md)
