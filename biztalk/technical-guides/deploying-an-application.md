---
title: "Deploying an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04bb4496-b1e9-400b-a849-a355381849ff
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deploying an Application
Deployment is the logistical distribution of application artifacts to ensure all necessary components are available to the systems that require them. These artifacts include BizTalk Server assemblies, .NET assemblies, schemas, maps, bindings, business rules, and certificates. The BizTalk application can be leveraged to help roll out artifacts to other computers added to the group or for staging (when transporting an application to another environment).  
  
 There are many ways to deploy BizTalk artifacts for example importing them as part of an application by using the Deployment Wizard (from an .msi file), importing them using BTSTask.exe, deploying them from Visual Studio, or using MSBuild. If you import them using BTSTask.exe or deploy them from Visual Studio, you can either specify an application to deploy them to, or leave the application name blank, in which case they will be deployed to the default application.  
  
## Deploying by Using an .msi File  
 With BizTalk Server, you can deploy an application and its artifacts by exporting them to an .msi file. (For more information about applications and artifacts, see [What is a BizTalk Application?](http://go.microsoft.com/fwlink/?LinkId=154994) (<http://go.microsoft.com/fwlink/?LinkId=154994>). Deployment of a BizTalk application involves importing the application artifacts into the BizTalk management database as well as installing the artifacts on each computer that is member of the group. Deploying to an .msi file serializes all of the application artifacts into one package. This can be performed by doing an Export operation from the Administration console or by using BTSTask.exe from the command line. Once you have an .msi file, you can deploy all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies to the BizTalk Management database for the group or run scripts specified to run at import time. This is done by using Microsoft Management Console (MMC) and doing an import operation of the .msi file (or via an import operation from the BTSTASK command line). The import operation of the .msi file creates the destination BizTalk application.  
  
 With the .msi file, you can deploy the application on a single computer, so that all BizTalk Server assemblies and dependency assemblies are stored in the Global Assembly Cache on the computer. The computer then has all of the binaries that it needs for run time. In this operation, you can also roll out Web services that are part of the solution, or apply computer-specific changes by scripts. This operation is performed by executing the .msi file. You can do this operation on each computer running BizTalk Server that is a member of the relevant BizTalk group. You can also use an .msi file to install an application on a new server added to a group.  
  
 If you are migrating your BizTalk application to a new group, you need to run the .msi installation on all servers in the new group. You need to import the .msi file once for the group. When you do, the application and its contents are installed on all run-time computers in the new group, and are also registered with the BizTalk Management database for the group. You can also add multiple binding files to an .msi file, in addition to the implicit bindings. Each additional binding file can be associated with an "environment". When multiple binding files are associated with a BizTalk Application during deployment, you can choose which binding files to use based on the environment (production, staging, or test) to which you are deploying.  
  
 You can use scripts with .msi files to customize a server (installation operation) or the group (import operation). For more information about using scripts with .msi files, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](http://go.microsoft.com/fwlink/?LinkId=154995) (http://go.microsoft.com/fwlink/?LinkId=154995).  
  
 For a checklist of steps for deploying an application, see [Checklist: Deploying an Application](../technical-guides/checklist-deploying-an-application.md).  
  
## Exporting an Application's Bindings by Using a Binding File  
 With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can export the bindings of an application to a binding file, and then import those bindings from the binding file to another application. To do so, the destination application must already exist; the import procedure does not create the application. The binding file is an XML file that contains the bindings of all artifacts in an application, group, or assembly. You can also export all bindings for a BizTalk group, or the bindings for a BizTalk assembly. For more information about working with bindings, see [How to Export Bindings to a Binding File](../technical-guides/how-to-export-bindings-to-a-binding-file.md) and [How to Import Bindings from a Binding File](../technical-guides/how-to-import-bindings-from-a-binding-file.md).  
  
 You can also add a binding file as a resource to an .msi file. For more information about adding a binding file as a resource, see [How to Export an Application to an .msi File](../technical-guides/how-to-export-an-application-to-an-msi-file.md).  
  
 For more information about application deployment in general, see [Understanding BizTalk Application Deployment and Management](http://go.microsoft.com/fwlink/?LinkId=154996) (http://go.microsoft.com/fwlink/?LinkId=154996).  
  
## In This Section  
  
-   [Best Practices for Deploying an Application](../technical-guides/best-practices-for-deploying-an-application.md)  
  
-   [Known Issues with Deploying an Application](../technical-guides/known-issues-with-deploying-an-application.md)  
  
-   [Permissions for Managing an Application](../technical-guides/permissions-for-managing-an-application.md)  
  
-   [Artifacts That Must Be Unique in an Application](../technical-guides/artifacts-that-must-be-unique-in-an-application.md)  
  
-   [Deploying and Exporting an Application](../technical-guides/deploying-and-exporting-an-application.md)