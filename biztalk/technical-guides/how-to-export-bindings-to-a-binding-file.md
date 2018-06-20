---
title: "How to Export Bindings to a Binding File | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3734ae6d-b790-40f2-8403-d7c7fdbe381b
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Export Bindings to a Binding File
You can export the bindings of a BizTalk application into another existing BizTalk application using a binding file. You can also export all the bindings in a group or the binding for an assembly. Subsequently, you can import those bindings into either an application or group.  
  
 A binding file is an XML file that describes the artifacts in the BizTalk Management database and their relationships. It contains binding information for each BizTalk Server orchestration, pipeline, map, or schema in the scope of a BizTalk assembly, application, or group. It contains the configuration settings for each send port, send port group, receive port, receive location, and party. It also describes which host each orchestration is bound to and its trust level.  
  
## Why to Export to a Binding File  
 Binding files can speed deployment in the following scenarios by avoiding the need to manually configure bindings:  
  
- **Moving an application from one deployment environment to another**  
  
   Using a binding file can speed deployment by avoiding the need to manually configure bindings for different deployment environments, such as from a development environment to a test environment.  
  
- **Updating an assembly**  
  
   You can use a binding file to automatically apply or reapply the bindings to an assembly after an update of the assembly.  
  
- **Deploying an assembly to multiple BizTalk groups**  
  
   You can avoid the need to separately configure the bindings for an assembly deployed into multiple BizTalk groups by using a binding file.  
  
  Using a binding file gives you flexibility in applying bindings to an application. When you export an application to an .msi file, you can only specify that all of the bindings for the application will be exported to the .msi file. With binding files you can do the following:  
  
- Export to a binding file all bindings from the current application, all bindings from the current group, or only the bindings for a single assembly. (You do so by using the Export Bindings command for an application in the Administration console.)  
  
- You can add a binding file to an application (using the Add Resources command) so that its bindings are applied immediately or so the bindings are applied when the application is imported into another group.  
  
- You can add multiple binding files to an application (using the Add Resources command) and specify a target deployment environment for each one. This enables you to use a single deployment package for multiple deployment environments. When you import the application, you can select which bindings to apply.  
  
- You can export separate binding files for multiple assemblies in an application.  
  
- You can edit binding files after you generate them to change their binding information.  
  
## How to Export to a Binding File  
 You export the bindings of an application to a binding file by executing the Export Bindings command for the application in the BizTalk Server Administration console, or by using the BTSTask ExportBindings command on the command line.  
  
 For security reasons, when you export a binding file, BizTalk Server removes the passwords for the bindings from the file. After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function. You configure passwords in the Transport Properties dialog box of the BizTalk Server Administration console for the send port or receive location.  
  
 Information in a binding file supersedes existing configuration information. If the name of an artifact in a binding file matches the name of an artifact in your existing configuration, the artifact in the binding file will update the artifact in your existing configuration when you import the binding file.  
  
 For information about how hosts and trust levels are stored in binding files, how host and trust levels in a binding file are matched to hosts and trust levels in the application, and the order in which bindings are applied, see [Binding Files and Application Deployment](http://go.microsoft.com/fwlink/?LinkID=154726) (http://go.microsoft.com/fwlink/?LinkID=154726). For instructions on how to export bindings for a BizTalk application, see [How to Export Bindings for a BizTalk Application](http://go.microsoft.com/fwlink/?LinkId=155009) (http://go.microsoft.com/fwlink/?LinkId=155009).