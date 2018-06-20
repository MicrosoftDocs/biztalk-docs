---
title: "Artifacts That Must Be Unique in an Application or Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "groups, artifacts"
  - "artifacts, requirements"
  - "applications, artifacts"
ms.assetid: a758cd74-a962-4e75-aea2-47752ab72a64
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Artifacts That Must Be Unique in an Application or Group
Certain types of artifacts in a BizTalk group or application must be unique, as follows:  
  
- Both BizTalk assemblies and non-BizTalk .NET assemblies must have a unique full name in the group. The full name consists of a file name, public key token, culture, and version.  
  
- Rules and policies must have a unique name and version number in the group.  
  
- Send ports, send port groups, receive ports, and receive locations must have a unique name in the group.  
  
- Web sites must have a unique virtual directory name in the group.  
  
- BAM resources must have a unique file name in the group.  
  
- Certificates must have a unique thumbprint in the group.  
  
- COM components must have a unique file name in the group.  
  
- File-based artifacts, such as scripts and other flat files, must have unique file names in the application, but not in the group.  
  
  You can specify the overwrite option to import or add an artifact to an application if the artifact already exists in the application and it is of a type that must be unique in an application. If the artifact already exists in another application in the group, and it is a type that must be unique in the group, you can neither add nor import it.  
  
  If you need to use an artifact in one application and it already exists in another application in the group, you can create a reference to the application containing the artifact. For more information see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).  
  
> [!NOTE]
>  You can view the full name of most types of artifacts in an application by using the ListApp command of BTSTask, as described in [ListApp Command](../core/listapp-command.md).  
  
## See Also  
 [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md)