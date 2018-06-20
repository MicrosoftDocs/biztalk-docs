---
title: "Updating Using Side-by-Side Versioning | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9721a091-98ec-4f0b-ad1f-6ca184956e7c
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Updating Using Side-by-Side Versioning
If you are not able to schedule downtime, or have very long-running orchestration instances that cannot be terminated, side-by-side versioning may be required. In this type of upgrade, two versions of the same application or application artifacts run side-by-side. The .NET runtime inherently allows for same-named but differently versioned assemblies to be deployed and running, and BizTalk Server also allows it.  
  
 Side-by-side versioning of applications is useful when you want to roll out a major application upgrade incrementally, for example making it available to a subset of business partners initially, rather than to all partners at once. Using this approach allows you to continue running the existing application to service the users who are not yet using the new version until you are ready to completely cut over to the new version.  
  
 You do not create application versions in the same manner that you create assembly versions, by incrementing the version number. Instead, you create a new application that has a different name from the original application, and populate it with the new versions of the application artifacts.  
  
 Because many types of artifacts, such as assemblies, can exist in only one application in a BizTalk group, you must increment the version number of any assemblies that already exist in the group before you can deploy them into the new application.  
  
 For a step-by-step list of tasks required to update an application or orchestration using side-by-side versioning, see [Checklist: Updating an Application Using Side-by-Side Versioning](../technical-guides/checklist-updating-an-application-using-side-by-side-versioning.md) and [Checklist: Updating an Orchestration Using Side-by-Side Versioning](../technical-guides/checklist-updating-an-orchestration-using-side-by-side-versioning.md). For detailed instructions on how to have side-by-side deployment of applications, see "[How to Deploy a New Version of an Application to Run Side-by-side with an Existing Version](http://go.microsoft.com/fwlink/?LinkId=155143) (<http://go.microsoft.com/fwlink/?LinkId=155143>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
## In This Section  
  
-   [How to Update a Map Using Side-by-Side Versioning](../technical-guides/how-to-update-a-map-using-side-by-side-versioning.md)  
  
-   [How to Update a Pipeline Using Side-by-Side Versioning](../technical-guides/how-to-update-a-pipeline-using-side-by-side-versioning.md)  
  
-   [Updating a Schema Using Side-by-Side Versioning](../technical-guides/updating-a-schema-using-side-by-side-versioning.md)