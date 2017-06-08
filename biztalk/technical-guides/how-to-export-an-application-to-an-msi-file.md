---
title: "How to Export an Application to an .msi File | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7179e86-aa55-426b-a0db-19229ca5625a
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Export an Application to an .msi File
You can use the Export MSI File Wizard or BTSTask to export the application artifacts into an .msi file that you will use to import the application into a new BizTalk group. This process will also install the application on the computers that will run it.  
  
## Exporting Application Bindings in an .msi File  
 When you export an application into an .msi file, you select which resources to export. These resources can include all or a subset of the deployed assemblies or bindings that are available for export.  
  
 To make it easier to import the applications back into your development environment at a later time to make changes or additions, you may want to export the bindings for each application and then add them back into the applications. When you set the Resource type to "BiztalkBinding," you can add additional binding files to an .msi file. For each binding file that you add, you must specify the environment name (text field) that the bindings should be applied to. Then on import, you will be asked to select the environment name to which you are presently importing. If these match, then the binding file is applied to the target group. You can also specify no environment name for the added binding file, which will cause the set of bindings to be applied to all environments unconditionally.  
  
 Using an .msi file automates what can otherwise be a substantial set of manual tasks. In a production environment, you can make it easier to deploy an assembly into multiple BizTalk groups by transporting the bindings for the assembly along with the assembly. If your application contains a significant number of artifacts, you can export some of the artifacts into one Windows Installer package and some into one or more other Windows Installer packages.  
  
 While exporting the application, you should consider some important points. For example, you may either export all of the artifacts in the application or only the artifacts that you want to add or update. If you export a file artifact, make sure that it is the version that you want to use in the application. For more such points and for more information about exporting a BizTalk application into an .msi file, see [How to Export a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154848) (http://go.microsoft.com/fwlink/?LinkID=154848).