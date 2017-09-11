---
title: "How to Create or Add an Artifact | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, artifacts"
  - "artifacts, creating"
  - "applications, artifacts"
ms.assetid: fea7487c-b5fa-457f-8c74-a20ea3a6df85
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create or Add an Artifact
After you create a BizTalk application, you can add file-based artifacts (for example BizTalk assemblies, .NET assemblies, scripts, and certificates) from the file system or add policies from the Rule Engine database. You can also create send ports, send port groups, receive locations, and receive ports within the application. Creating or adding artifacts adds them to the BizTalk Management database. You can then deploy the application and its artifacts as a single entity, as described in [Deploying BizTalk Applications](../core/deploying-biztalk-applications.md).  
  
> [!NOTE]
>  Certain types of artifacts must be unique in a BizTalk application or group. For more information, see [Artifacts That Must Be Unique in an Application or Group](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).  
  
 For procedures on adding or creating each artifact type, see the following topics:  
  
-   [How to Create a Send Port](../core/how-to-create-a-send-port2.md)  
  
-   [How to Create a Send Port Group](../core/how-to-create-a-send-port-group.md)  
  
-   [How to Create a Receive Port](../core/how-to-create-a-receive-port.md)  
  
-   [How to Create a Receive Location](../core/how-to-create-a-receive-location.md)  
  
-   [How to Add a Policy to an Application](../core/how-to-add-a-policy-to-an-application.md)  
  
-   [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md)  
  
-   [How to Add a Pre- or Post-processing Script to an Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)  
  
-   [How to Add a File to an Application](../core/how-to-add-a-file-to-an-application.md)  
  
-   [How to Add a Certificate to an Application](../core/how-to-add-a-certificate-to-an-application.md)  
  
-   [How to Add a COM Component to an Application](../core/how-to-add-a-com-component-to-an-application.md)  
  
-   [How to Add a .NET Assembly to an Application](../core/how-to-add-a-net-assembly-to-an-application.md)  
  
-   [How to Add a BAM Artifact to an Application](../core/how-to-add-a-bam-artifact-to-an-application.md)  
  
-   [How to Add a Binding File to an Application](../core/how-to-add-a-binding-file-to-an-application2.md)  
  
> [!NOTE]
>  If the artifact you are adding has a very long path (e.g., the path and file name), the operation to add the artifact to an application may fail. A path can't exceed 260 characters.  
  
## See Also  
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)   
 [How to Add a 64-Bit Artifact to an Application](../core/how-to-add-a-64-bit-artifact-to-an-application.md)