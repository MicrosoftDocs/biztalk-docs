---
title: "BTAD_HostClass | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BTAD_HostClass [environment variable]"
ms.assetid: 068a19e9-2566-4c8e-a8b4-fd2fa614e8ed
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BTAD_HostClass
BTAD_HostClass indicates whether the operation is being performed on the BizTalk Management database or the local computer.  
  
## Remarks  
 The following table describes the possible values for BTAD_HostClass.  
  
|Value|Description|  
|-----------|-----------------|  
|ConfigurationDb|Specifies that the import operation is being performed on the BizTalk Management database for the group|  
|BizTalkHostInstance|Specifies that the install or uninstall operation is being performed on the local computer|  
  
## See Also  
 [Pre- and Post-processing Script Environment Variables](../core/pre-and-post-processing-script-environment-variables.md)   
 [How Environment Variables Indicate Deployment State](../core/how-environment-variables-indicate-deployment-state.md)