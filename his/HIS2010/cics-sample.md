---
title: "CICS Sample | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56031689-b800-4507-9624-389510a7a8cf
caps.latest.revision: 3
---
# CICS Sample
The CICS sample describes how to compile and access the Woodgrove Bank CICS using host-initiated processing.  
  
## Location in SDK  
 \<installation directory>:\Program Files\Microsoft Host Integration Server\SDK\Samples\ApplicationIntegration\HostInitiated\CICS  
  
## File Inventory  
 The following table shows the files in the sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|In the /CICSBanking folder<br /><br /> CICSBanking.csproj<br /><br /> CICSBanking.sln<br /><br /> CICSBanking.suo<br /><br /> CICSBankingExceptions.cs<br /><br /> Class1.cs<br /><br /> Readme-01-VTAM-LU0-LU2-Setup.txt<br /><br /> Readme-02-CICS-LU0-LU2-Setup.txt<br /><br /> Readme-06-Configure-HIS.txt<br /><br /> ReadMeSNA.txt<br /><br /> REadMeTCPIP.txt|The files that contain the sample application. The readme files describe the different setup and support files necessary for the various configurations.|  
|In the /CICSBanking/Properties folder<br /><br /> AssemblyInfo.cs|Contains the assembly information for the sample application.|  
|In the /CICSBanking/TIClientDefs folder<br /><br /> MSHIPLNK.cbl<br /><br /> MSHIPLNK.lkd<br /><br /> TIClientDefs.tiproj<br /><br /> WBCLKNPS.cbl<br /><br /> WBCLKNPS.lkd<br /><br /> WBCLKNPT.cbl<br /><br /> WBCLNKNPT.lkd<br /><br /> WBCUDPCS.cbl<br /><br /> WBCUBPCS.lkd<br /><br /> WBCUDPCT.cbl<br /><br /> WBCUDPCT.lkd<br /><br /> wgbmaps.bms<br /><br /> wgmaps.lkd|Contains the files that describe the programs, transitions, and maps for the host application.|  
|In the /CICSBanking/TIServerDefs<br /><br /> CICSBanking.DLL<br /><br /> CICSBanking.TIM<br /><br /> TIServerDefs.tiproj|Contains the support files that describe the remote host application to the sample application.|