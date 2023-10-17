---
description: "Learn more about: Adding Artifacts to an Application"
title: "Adding Artifacts to an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9b5e92e-2e55-41d7-9959-f62753bbeb04
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adding Artifacts to an Application
You can add and configure artifacts, such as send and receive ports, receive locations, and orchestrations, by using the Administration console. You can also generate binding files and add them to the application if you want to apply different bindings for the different environments that you will import the application into.

 You can add additional (typically non-BizTalk Server) artifacts, such as scripts, certificates, and Readme files, to the application under the Resources node. To do so, use the Administration console or BTSTask.

 For more information about artifacts, see [How to Create or Add an Artifact](../core/how-to-create-or-add-an-artifact.md) (https://go.microsoft.com/fwlink/?LinkID=154724), [Managing Artifacts](../core/managing-artifacts.md) (https://go.microsoft.com/fwlink/?LinkID=154725) and [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md) (https://go.microsoft.com/fwlink/?LinkID=154726).

## Factoring Artifacts into Multiple BizTalk Applications
 During the development process, you may have deployed your assemblies into a single application for convenience. For various reasons, you may want to factor the artifacts into multiple applications before they are deployed into production.

 Before deploying, you should perform an in-depth analysis of the factoring of an assembly. Determine whether you should perform No factoring, Full factoring, or Optimal factoring.

 **No Factoring**

 All BizTalk artifacts are in one assembly. This is the easiest to understand and deploy, but provides the least amount of flexibility.

 **Full Factoring**

 Each BizTalk artifact is in its own assembly. This provides the most flexibility, but is the most complex to deploy and understand.

 **Optimal Factoring**

 Optimal factoring falls between No Factoring and Full Factoring based on in-depth analysis of your BizTalk applications. In addition to versioning, this allows you to more easily implement your BizTalk host design. This is achieved by looking for relationships among BizTalk artifacts. If possible, put artifacts that are always versioned together in the same assembly. If independent versioning of the artifacts is required, then they must be put in different assemblies. This is the level of factoring that you want to achieve.