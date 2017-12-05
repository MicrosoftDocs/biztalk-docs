---
title: "Batch Sample | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d052adc1-f2a7-4f82-9ec5-385747730073
caps.latest.revision: 4
---
# Batch Sample
The Batch sample describes how to use TCP/IP HIP client programs in conjunction with batch files on the host server.  
  
## Location in SDK  
 \<installation directory>:\Program Files\Microsoft Host Integration Server 2010\SDK\Samples\ApplicationIntegration\HostInitiated\Batch  
  
## File Inventory  
 The following table shows the files in the sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|In the /BatchBanking folder<br /><br /> BatchBanking.csproj<br /><br /> BatchBanking.sln<br /><br /> BatchBanking.suo<br /><br /> BatchBAnkingException.cs<br /><br /> Class1.cs<br /><br /> Meadme.txt<br /><br /> TI_HIP_SQLServer.sql|The files that contain the sample client application. The readme files describe the different setup and support files necessary for the various configurations. The SQL file contains the sample database.|  
|In the /BatchBanking/Properties folder<br /><br /> AssemblyInfo.cs|Contains the assembly information for the sample application.|  
|In the /BatchBanking/TIClientDefs folder<br /><br /> alloc.jcl<br /><br /> delete.jcl<br /><br /> gaccclie.jcl<br /><br /> gbalcle.jcl<br /><br /> getaccoud.cbl<br /><br /> getaccud.ldk<br /><br /> getbalk.cbl<br /><br /> getbalk.lkd<br /><br /> mshiplkb.cbl<br /><br /> mshiplkb.lkd<br /><br /> mshipudb.cbl<br /><br /> mshipudb.lkd<br /><br /> prtvsam.jcl<br /><br /> TIClientDefs.tiproj|Contains the batch files for the remote host.|  
|In the /BatchBanking/TIServerDefs<br /><br /> BatchBanking.DLL<br /><br /> BatchBanking.TIM<br /><br /> TIServerDefs.tiproj|Contains the support files that describe the remote host application to the sample application.|  
  
## See Also  
 [Application Integration Samples](../core/application-integration-samples.md)