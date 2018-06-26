---
title: "How to Update a Pipeline Using Side-by-Side Versioning | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd884a76-71dd-4c90-b4ba-f1cd7f48eb04
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Update a Pipeline Using Side-by-Side Versioning
The simple way to use a new pipeline added by side-by-side versioning is to select the newly deployed pipeline version in the send port or receive location. This will replace the old pipeline with the new one. However, if you need true side-by-side functionality for backwards-compatibility, then you must create new send ports and receive locations and bind them to the new pipeline version specified.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.  
  
### To add a new version of a pipeline component  
  
1. In Visual Studio, create a new version of the pipeline component, and sign the assembly.  
  
2. Add the pipeline component in the **Pipeline Components** folder (\<*installation folder*\>\Pipeline Components).  
  
3. Add the pipeline component to your pipeline.  
  
4. After building the pipeline or deploying your solution, remove the pipeline component from the **Pipeline Components** folder.  
  
5. Add the pipeline component to the global assembly cache (GAC).  
  
   After you have completed these steps, the compiled pipeline assembly will refer to the correct version of the pipeline component, and the AppDomain used by BizTalk Server will find the new version of the pipeline component in the GAC, rather than finding the previous version of the pipeline component in the Pipeline Components folder.  
  
## See Also  
 [Updating Using Side-by-Side Versioning](../technical-guides/updating-using-side-by-side-versioning.md)