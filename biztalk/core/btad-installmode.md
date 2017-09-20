---
title: "BTAD_InstallMode | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BTAD_InstallMode [environment variable]"
ms.assetid: b0ca48b8-c672-4704-9a04-2c6f159e57be
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BTAD_InstallMode
BTAD_InstallMode describes the installation mode for BizTalk application deployment.  
  
## Remarks  
 The following table describes the possible values for BTAD_InstallMode.  
  
|Value|Description|  
|-----------|-----------------|  
|Install|Create or update to BizTalkHostInstance (the local computer)|  
|Import|Create or update to ConfigurationDb (the BizTalk Management database for the group)|  
|Uninstall|Delete from BizTalkHostInstance (the local computer)|  
  
## See Also  
 [Pre- and Post-processing Script Environment Variables](../core/pre-and-post-processing-script-environment-variables.md)   
 [How Environment Variables Indicate Deployment State](../core/how-environment-variables-indicate-deployment-state.md)