---
title: "InstallationVerification Sample | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3790abe-e954-420c-a185-855b00214985
caps.latest.revision: 4
---
# InstallationVerification Sample
The InstallationVerification sample describes how to verify an installation of an application on a remote host.  
  
## Location in SDK  
 \<installation directory>:\Program Files\Microsoft Host Integration Server\SDK\Samples\ApplicationIntegration\WindowsInitiated\InstallationVerification  
  
## File Inventory  
 The following table shows the files in the sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|In the /InstallationVerification folder<br /><br /> InstallationVerification.csproj<br /><br /> InstallationVerification.sln<br /><br /> InstallationVerification.suo<br /><br /> Program.cs<br /><br /> Readme-01-First.txt<br /><br /> Readme-02-VTAM-Setup.txt<br /><br /> Readme-03-CICS-SNA-Setup.txt<br /><br /> Readme-04-IMS-SNA-Setup.txt<br /><br /> Readme-05-Configure-HIS.txt<br /><br /> Readme-06-TCPIP-Setup.txt<br /><br /> Readme-07-CICS-TCPIP-Setup.txt<br /><br /> Readme-08-IMS-TCPIP-Setup.txt<br /><br /> Readme-09-OS400-TCPIP-Setup.txt|The files that contain the sample application. The readme files describe the different setup and support files necessary for the various configurations.|  
|In the /InstallationVerification/Properties folder<br /><br /> AssemblyInfo.cs|Contains the assembly information for the sample application.|  
|In the /InstallationVerification/TIHostApplicationDef folder<br /><br /> CICSSNALink.cbl<br /><br /> CICSSNALink.lkd<br /><br /> CICSSNAUserData.lkd<br /><br /> CICSTCPUserDAta.cbl<br /><br /> CICSTCPUserDAta.lkd<br /><br /> IMS.cbl<br /><br /> IMS.lkd<br /><br /> IMSCONV.cbl<br /><br /> IMSCONV.lkd<br /><br /> ivp.exe<br /><br /> IVP_CICS_ELMLink.dll<br /><br /> IVP_CICS_SNALink.dll<br /><br /> IVP_CICS_SNAUserData.dll<br /><br /> IVP_CICS_TRMLink.DLL<br /><br /> IVP_CICS_TRMUserData.DLL<br /><br /> IVP_CICS_IMSConnect.dll<br /><br /> IVP_CICS_SNAUserData.dll<br /><br /> IVP_OS400_DCP.dll<br /><br /> Mscmtics.cbl<br /><br /> Mscmtics.lkd<br /><br /> OS400DCP.rpg<br /><br /> TiHostApplicationDefltiproj<br /><br /> WIPExportedConfig.xml|Contains the support files that describe the remote host application to the sample application.|  
  
## See Also  
 [Windows-Initiated Processing Samples](../core/windows-initiated-processing-samples.md)