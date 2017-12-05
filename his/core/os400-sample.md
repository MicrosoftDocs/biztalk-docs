---
title: "OS400 Sample | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3890126a-4f1a-4e00-af94-f6b75830a924
caps.latest.revision: 4
---
# OS400 Sample
The OS400 sample describes how to verify an installation of an application on a remote host.  
  
## Location in SDK  
 \<installation directory>:\Program Files\Microsoft Host Integration Server\SDK\Samples\ApplicationIntegration\HostInitiated\OS400  
  
## File Inventory  
 The following table shows the files in the sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|In the /OS400/OS400Banking folder<br /><br /> Class1.cs<br /><br /> OS400Banking.csproj<br /><br /> OS400Banking.sln<br /><br /> OS400Banking.suo<br /><br /> OS400BankingException.cs<br /><br /> ReadMeTCPIP.txt|The files that contain the sample application. The readme files describe the different setup and support files necessary for the various configurations.|  
|In the /OS400Banking/Properties folder<br /><br /> AssemblyInfo.cs|Contains the assembly information for the sample application.|  
|In the /OS400/TIClientDefs folder<br /><br /> Mshiplnk.rpg<br /><br /> qrpglesrc_ernno_h.txt<br /><br /> qrpglesrc_socket_h.txt<br /><br /> qrpglesrc_socketutil_h.txt<br /><br /> qrpglesrc_socketutilr4.txt<br /><br /> TIClientDefs.tiproj<br /><br /> wbclknpt.rpg<br /><br /> wgbmaps.scr|Contains the files that describe the remote host application.|  
|In the /OS400/TIServerDefs folder<br /><br /> OS400Banking.DLL<br /><br /> OS400Banking.TIM<br /><br /> TIServerDefs.tiproj|Contains the support files that describe the remote host application to the sample application.|  
  
## See Also  
 [Application Integration Samples](../core/application-integration-samples.md)