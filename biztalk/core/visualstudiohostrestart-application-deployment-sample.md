---
description: "Learn more about: VisualStudioHostRestart (Application Deployment Sample)"
title: "VisualStudioHostRestart (Application Deployment Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0b82627-1552-479d-a083-cdc9fe4843c3
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# VisualStudioHostRestart (Application Deployment Sample)
This topic explains how to use the VisualStudioHostRestart sample script to restart a host instance running under [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on the local computer. You can use this script when redeploying assemblies in Visual Studio so that the BizTalk Server runtime immediately picks up the changes. Alternatively, you can use the option to restart host instances, which you can set in Deployment properties for the project. For more information, see [How to Set Deployment Properties in Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md).  
  
## What This Sample Does  
 This sample script performs the following actions, in order:  
  
1.  Stops all in-process host instances on the local computer.  
  
2.  Starts all in-process host instances on the local computer.  
  
## Where to Find This Sample  
 The sample is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder, as follows: *\<Samples path\>*\Application Deployment\VisualStudioHostRestart.  
  
 The sample includes the following file:  
  
-   RestartBizTalkHostInstances.vbs  
  
## How to Use This Sample  
 Use the following procedures to run this sample.  
  
### To run the sample  
  
-   Run RestartBizTalkHostInstances.vbs.  
  
## See Also  
 [Application Deployment (BizTalk Server Samples Folder)](../core/application-deployment-biztalk-server-samples-folder.md)   
 [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)   
 [Deploying BizTalk Applications](../core/deploying-biztalk-applications.md)
