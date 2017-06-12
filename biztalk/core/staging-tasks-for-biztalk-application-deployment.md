---
title: "Staging Tasks for BizTalk Application Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications, staging"
  - "deploying [applications], staging"
  - "applications, deploying"
  - "deploying [applications], tasks"
ms.assetid: de60eddb-da13-412a-94f9-331387b5930e
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Staging Tasks for BizTalk Application Deployment
The following are the steps involved in deploying a BizTalk application to a staging environment.  
  
1.  **Copy the .msi file to your staging environment.** As described in [Testing Tasks for BizTalk Application Deployment](../core/testing-tasks-for-biztalk-application-deployment.md), when the BizTalk application has completed testing and is ready for staging, the test team provides one or more .msi files for staging. (A complete solution may consist of one or more BizTalk applications, so you may receive several .msi files to stage.)  You can copy this .msi file onto your staging computers, and then, as described in the next step, import the BizTalk application from the .msi file into a BizTalk group in the staging environment. You also use the .msi file to install the application onto the computers that are to run the application.  
  
2.  **Import the application from the .msi file.** You can use the Import Wizard, available from the BizTalk Server Administration console, to import the contents of the .msi file into an application into a BizTalk group in the staging environment. For more information, see [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md). If the specified application does not already exist, importing the .msi file creates it. You can then view the application and modify its configuration and contents from the BizTalk Server Administration console. You might need to do this, for example, to modify the bindings for your staging environment. For more information, see [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md). If a binding file was added to the application that has the appropriate bindings for your staging environment, you can apply the bindings during the import process. For more information, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).  
  
3.  **Export binding files and add them back into the application (optional).** To make it easier to import the application back into your staging environment at a later time if changes or additions are made to the application, you may want to export the application bindings and then add them back into the application, specifying a Staging target environment for the bindings. When you later import the application .msi file back into BizTalk Server in your staging environment, you can specify that these bindings be applied. For more information, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).  
  
4.  **Install the application.** You can now install the application on all of the computers that will run the application. You can install the application by using the Installation Wizard or simply double-clicking the .msi file. For more information, see [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md).  
  
5.  **Test the application to verify the configuration and bindings.** You can now test the application to make sure it is functioning as expected in the staging environment. After you or the developer makes any required changes, you can follow steps 1 through 4 again.  
  
6.  **Generate an .msi for deploying the application to the production environment**. Once you have finished configuring your BizTalk application for the production environment and verified the configuration, you can deploy it to your production environment. To do this, you use the Export Wizard to generate a new .msi file, as described in [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md). You can then hand off the .msi file to the IT administrator responsible for production deployment. The IT administrator will use the .msi file to import the application into BizTalk Server on production computers, as well as install it on the computers that will run it, as described in [Production Tasks for BizTalk Application Deployment](../core/production-tasks-for-biztalk-application-deployment.md).  
  
## See Also  
 [Application Deployment Tasks](../core/application-deployment-tasks.md)