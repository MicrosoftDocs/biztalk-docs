---
title: "Updating an Artifact | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40feab57-4286-4bdf-8f52-25d02b3fa60c
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Updating an Artifact
Dependencies between artifacts in two or more BizTalk applications can have a significant effect on application deployment and maintenance. An artifact is dependent on another when it needs to use that artifact in order to function properly, for example an orchestration that needs to use a specific pipeline in order to transmit messages correctly.  
  
 To update an artifact in an application, you must first undeploy it, along with any artifacts that depend on it. When artifacts that have dependencies exist in the same application, BizTalk Server automatically handles the undeployment and redeployment tasks for the updated and dependent artifacts. When artifacts that have dependencies exist in different applications, however, this is not the case. If you want to update an artifact in one application, and an artifact in another application has a dependency on it, you must undeploy and redeploy the dependent artifact manually as follows:  
  
1. Stop, unenlist, and unbind the dependent artifact.  
  
2. Update the artifact on which it depends.  
  
3. Bind, enlist, and start the dependent artifact.  
  
   To avoid the need to perform manual steps to update an artifact on which other artifacts depend, you can try to keep all artifacts with dependencies together in the same application. This is not always possible, however, because most types of artifacts must be unique in a BizTalk group. You cannot have the same artifact in two different applications in the same group, even if both applications contain artifacts that depend on the same artifact. For more information about the issue of unique artifacts, see [Artifacts That Must Be Unique in an Application or Group](http://go.microsoft.com/fwlink/?LinkId=155141) (<http://go.microsoft.com/fwlink/?LinkId=155141>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
   You can add the needed artifact to one application and then add a reference to that application from any other applications containing artifacts that depend on it. When you add a reference to an application, artifacts in the application can use any artifacts in the application that it references. For instructions on adding a reference, see [How to Add a Reference to Another Application](http://go.microsoft.com/fwlink/?LinkID=155011) (<http://go.microsoft.com/fwlink/?LinkID=155011>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
   For a checklist of tasks for updating artifacts in a BizTalk application, see [Checklist: Update the Artifacts in a BizTalk Application](http://go.microsoft.com/fwlink/?LinkId=155647) (<http://go.microsoft.com/fwlink/?LinkId=155647>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
## See Also  
 [Updating Applications and Artifacts](../technical-guides/updating-applications-and-artifacts.md)