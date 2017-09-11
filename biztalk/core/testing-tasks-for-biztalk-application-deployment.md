---
title: "Testing Tasks for BizTalk Application Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying [applications], testing"
  - "testing, deploying"
  - "testing, tasks"
ms.assetid: fb043755-6d01-4ceb-b189-5a5f286c2b37
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Testing Tasks for BizTalk Application Deployment
The following are the steps involved in deploying the artifacts of a BizTalk application to a test environment for testing and debugging.  
  
1.  **Copy the .msi file to your test environment.** As described in [Development Tasks for BizTalk Application Deployment](../core/development-tasks-for-biztalk-application-deployment.md), when a BizTalk application is ready to test, the developer exports the application artifacts into an .msi file. A complete solution may consist of one or more BizTalk applications, so you may receive several .msi files to test. You can copy the .msi file onto your test computer, and then, as described in the next step, import the artifacts from the .msi files into BizTalk Server. You also use the .msi files to install the applications onto the computers that are to run them.  
  
2.  **Import the application from the .msi file.** You can use the Import Wizard, available from the BizTalk Server Administration console, to import the artifacts in the .msi file into an application on the current instance of BizTalk Server. For more information, see [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md). If the specified application does not already exist, the importing process creates it. You can then view the application and modify its configuration and contents from the BizTalk Server Administration console. You might need to do this, for example, to modify the bindings for your test environment. For more information, see [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md). If a binding file was added to the application that has the appropriate bindings for your test environment, you can apply the bindings during the import process. For more information, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).  
  
3.  **Install the application.** You can now install the application on servers on which you want to run the application. If the application includes file-based artifacts, you must install it or it will not function. You can install the application by double-clicking the .msi file. This installs and registers the application's artifacts on the local computer so that the application can run. For more information, see [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md).  
  
4.  **Test the application.** You can now test the application. After the developer fixes any bugs that you find and gives you an updated .msi file, you can take steps 1, 2, and 3 again.  
  
5.  **Export binding files and add them back into the application (optional).** To make it easier to import the application back into your testing environment at a later time if you need to test changes or additions, you may want to export the application bindings and then add them back into the application, specifying a Test target environment for the bindings. When you later import the application .msi file back into BizTalk Server in your test environment, you can specify that these bindings be applied. For more information, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).  
  
6.  **Generate an .msi for deploying the application to the staging environment**. Once you have finished testing your BizTalk application, you can deploy it to a staging environment. To do this, you use the Export Wizard to generate a new .msi file, as described earlier in step 2. You can then hand off the .msi file to the IT administrator responsible for staging deployment. The IT administrator will use the .msi file to import the application into BizTalk Server on staging computers and install the application on the computers that will run it, as described in [Staging Tasks for BizTalk Application Deployment](../core/staging-tasks-for-biztalk-application-deployment.md).  
  
## See Also  
 [Application Deployment Tasks](../core/application-deployment-tasks.md)