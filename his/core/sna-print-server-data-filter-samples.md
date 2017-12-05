---
title: "SNA Print Server Data Filter Samples | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6d93d40-c576-4678-a2bf-e8be09fa00ce
caps.latest.revision: 5
---
# SNA Print Server Data Filter Samples
The PrintServer sample illustrates features of the SNA Print Server Data Filter API. These features can be used to extend the capabilities of the Host Print Service in [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]. The sample code illustrates how to write a print data filter dynamic-link library (DLL) that will be called by Host Print Service when a print job is initiated, when data is sent to the printer, and when the print job is completed.  
  
## Location in the SDK  
 \<installation directory>\Program Files\\<version\>\SDK\Samples\NetworkIntegration\PrintServer  
  
## File Inventory  
  
|File(s)|Description|  
|---------------|-----------------|  
|In the /PrintServer/PrintDefFile directory<br /><br /> Hplj2.pdf|The sample file to print|  
|In the /PrintServer/PrnFltr directory<br /><br /> Makefile<br /><br /> NTFilter.c<br /><br /> NTFilter.Def<br /><br /> NtFilter.h<br /><br /> NTFilter.Mdp<br /><br /> NTFilter.rc<br /><br /> Prntfltr.sln<br /><br /> Prntfltr.vcproj|The sample application an related files, The sample program written in C that illustrates use of the SNA Print Server Data Filter API.<br /><br /> Also includes an include file with function defines, a resource file, a command-line makefile, and a project file.|  
  
## How to Use the Sample  
 The PrnFltr sample is designed to be built using Visual Studio.  
  
#### To build the PrnFltr sample using the command-line compiler  
  
1.  Open a command prompt window  
  
2.  Run VSVARS32.bat from the Visual Studio bin directory  
  
     by default, the location is C:\Program Files\Microsoft Visual Studio\Common7\Tools  
  
3.  Navigate to \PrintServer\PrnFlter subdirectory, and invoke NMAKE  
  
#### To build the PrnFltr sample using Visual Studio  
  
1.  open the appropriate Visual C++ project file (PrintServer\PrnFltr\ntfilter.vcproj) from the **File** menu.  
  
2.  Select a configuration and build the sample from the **Build** menu.  
  
     Each project file has two configurations, one for a DEBUG build and one for a RETAIL build.  
  
## See Also  
 [Network Integration Samples](../core/network-integration-samples.md)   
 [SNA Print Server Data Filter Programmer's Reference](../core/sna-print-server-data-filter-programmer-s-reference2.md)   
 [SNA Print Server Data Filter Programmer's Guide](../core/sna-print-server-data-filter-programmer-s-guide1.md)