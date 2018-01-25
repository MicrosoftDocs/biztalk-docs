---
title: "Contents of IHVLinks Sample Kit on Host Integration Server1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bac0ffb5-0e46-45c8-b509-4aa3b966bc00
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Contents of IHVLinks Sample Kit on Host Integration Server
You can view the sample source code for a generic Synchronous Data Link Control (SDLC) integrated link configuration Windows Installer (MSI) package that illustrates an integrated independent hardware vendor (IHV) link service installation. These files are copied to your hard drive during Host Integration Server software or Host Integration Client software installation when the Host Integration Server Software Development Kit (SDK) option is selected. These samples are installed in the SDK\Samples\IHVLinks subdirectory below where the Host Integration Server SDK software is installed (C:\Program Files\\Host Integration Server\SDK, by default).  
  
 These sample files include the following directories.  
  
|Directory|Description|  
|---------------|-----------------|  
|**LinkServ**|Directories used in creating the IHVLinks sample generic SDLC link service configuration and detection DLLs.|  
|**LinkServ\Build**|A file containing the normal COFF base address for a link service configuration DLL (linkcfg).|  
|**LinkServ\Detect**|The source code to the sample generic SDLC link service detection DLL.|  
|**LinkServ\Linkcfg**|The source code to the sample generic SDLC link service configuration DLL. The link service configuration DLL must export specific functions. A definitions (.DEF) file must be used so that exported function names are not decorated by the compiler and linker.|  
|**LinkServ\LnkTools**|The source code to a collection of library routines used by the generic SDLC link service configuration DLL.|  
|**LinkServ\NT5INF**|An INF file that can be used with the generic SDLC link service.|  
|**Setup**|Directories used in creating the IHVLinks sample generic SDLC link service setup and setup test tools.|  
|**Setup\Bins**|The compiled generic MSI package containing the generic SDLC link service driver, configuration and detection DLLs, and configuration tool.|  
|**Setup\CASource**|This directory contains the source code used for the custom actions in setup. The GetHISData custom action sets the MSI property SERVER_INSTALLED to "YES" if Host Integration Server is installed; otherwise the property is set to "NO". This custom action is used to disable Host Integration Server dependent features from the installation directory if not installed.<br /><br /> The SetHISPath custom action sets the target directory INSTALLDIR1 to the installation directory where Host Integration Server was installed. This custom action is used to set the destination directory for the link service configuration DLLs.|  
|**Setup\Package**|The sample GENERIC.MSI SDLC link service package ready for installation and testing.|  
|**Setup\Tools**|The source code for various utility functions and tools that can be used to test your integrated link service MSI package.|  
  
 This sample source code is included for your reference. The communication between workstation management station and Host Integration Server is performed by RPCSVC.EXE, the SNA remote procedure call (RPC) service.