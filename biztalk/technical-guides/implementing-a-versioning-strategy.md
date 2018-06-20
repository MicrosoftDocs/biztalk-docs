---
title: "Implementing a Versioning Strategy | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a3c7af6-6277-4667-8f14-e6d1cb9e99d4
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Implementing a Versioning Strategy
Versioning is the act of updating the implementation of an artifact and incrementing its version number.  
  
## General Versioning Issues  
 BizTalk application versioning can become an issue when you need to run two versions of a BizTalk solution side-by-side, or if you cannot schedule BizTalk application downtime to deploy a new version. If you do not need to run two versions of the solution simultaneously (for example, if you have no long-running orchestrations), then it is perfectly acceptable to undeploy the old version and deploy the new version as a versioning strategy (no assembly versioning). This is a possible versioning strategy, although we still recommend incrementing the file version number (to let you know which version is deployed on the BizTalk servers). For more information about updating an application that is deployed, see [Checklist: Updating an Assembly](../technical-guides/checklist-updating-an-assembly.md).  
  
 If you need to support long-running orchestrations, and/or you need to perform BizTalk application deployments with no BizTalk application downtime, then a solid BizTalk versioning strategy needs to be implemented and practiced end-to-end for the different versioning scenarios. This includes .NET assembly versioning and versioning of all BizTalk artifacts. This includes schemas, maps, pipelines, pipeline components, orchestrations, custom adapters, custom classes called in orchestrations and maps, business rules, and BAM. For more information about side-by-side versioning, see [Updating Using Side-by-Side Versioning](../technical-guides/updating-using-side-by-side-versioning.md).  
  
## Versioning an Assembly  
 When you update an assembly, you have a choice between the following:  
  
- Choosing a fixed assembly version for a given deliverable and incrementing only the file version number.  
  
- Incrementing both the assembly version and the file version during the course of development.  
  
  These approaches are compared in the following table:  
  
|**Fixed assembly version, dynamic file version**|**Dynamic assembly version, fixed or dynamic file version**|  
|------------------------------------------------------|-----------------------------------------------------------------|  
|Assembly version number = Fixed number<br /><br /> File version number = Build number|Assembly version number = Build number<br /><br /> File version number = Build number|  
|BizTalk Server runtime may pick up the wrong version of the assembly if multiple assemblies are installed.|BizTalk Server always runs the latest version of the assembly, even if multiple assemblies are installed.|  
|Only one version of the solution can be deployed at any time.|Different versions of the solution can be deployed side by side (although other aspects of the solution, such as schema definitions, may conflict).|  
|BizTalk Host needs to be restarted to force the loading of updated assemblies.|Forces BizTalk Server to load new assemblies.|  
|Requires less work to create a new deployment because files that reference the assembly version number (for example, binding files and tracking profiles) do not need to be edited.|Requires more work for deployment because files that reference the assembly version number need to be kept updated with the new version.|  
  
 You may choose to use the fixed assembly version and dynamic file version approach if you are prototyping a system or developing any other type of project that will not be released. If you do not intend to deliver the application to an end user, you can streamline deployment tasks and reduce broken dependencies by fixing the assembly version and incrementing the file version number. For version tracking, you must remember to increment the file version number for each build.  
  
 If you are building a project that will be delivered to an end user, you should consider incrementing the assembly version number and, optionally, storing a meaningful file version number. While this approach incurs the added effort of modifying build numbers and associated dependencies, it ensures that the latest versions of your assemblies are used. By using automated deployment scripts, you can lessen the impact of versioning. To view deployment samples, see [Application Deployment (BizTalk Server Samples Folder)](http://go.microsoft.com/fwlink/?LinkId=155134) (<http://go.microsoft.com/fwlink/?LinkId=155134>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
> [!NOTE]  
>  You should choose the versioning mechanism that ensures that the proper files are delivered and that simplifies maintenance and enhancement.  
  
 For more information about versioning issues, see [BizTalk Server Project Versioning](http://go.microsoft.com/fwlink/?LinkID=154209) (<http://go.microsoft.com/fwlink/?LinkID=154209>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.