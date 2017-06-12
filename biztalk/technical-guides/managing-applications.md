---
title: "Managing Applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef1039fb-7460-444b-a45e-2783bdc7c109
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing Applications
A BizTalk application is a logical container for application artifacts, such as orchestrations, pipelines, schemas, maps, and ports. BizTalk applications enable you to include related components in the same container. Any artifact within an application may refer to any other artifacts within that application, or to any artifact in any referenced application. For a complete list of artifacts that can be in a BizTalk application, see [What is a BizTalk Application?](http://go.microsoft.com/fwlink/?LinkId=154994) (http://go.microsoft.com/fwlink/?LinkId=154994).  
  
 BizTalk applications streamline many everyday [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tasks. You can deploy, manage, start, stop, and troubleshoot [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] at the application level. This results in less confusion and less risk of error for users. A BizTalk application container contains  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies that are deployed to it by the Visual Studio environment. The application may also contain receive ports, receive locations, send ports, property tracking settings, and role links. You can manually add [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies to the application, or move [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies from other applications. In addition, you can add non-[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] artifacts such as Business Rule Engine (BRE) policies and BAM definition files. Implicitly, the application also contains all of the bindings that are represented by their current settings.  
  
 You can create pre- or post-processing scripts to perform actions when an application is imported, installed, or uninstalled. For more information about using such scripts, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](http://go.microsoft.com/fwlink/?LinkId=154995) (http://go.microsoft.com/fwlink/?LinkId=154995).  
  
 This section describes how to deploy, version, and update applications or individual artifacts.  
  
## In This Section  
  
-   [Deploying an Application](../technical-guides/deploying-an-application.md)  
  
-   [Updating an Application](../technical-guides/updating-an-application.md)