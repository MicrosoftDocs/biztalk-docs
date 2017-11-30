---
title: "Building the TPs (CPI-C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7038b8a2-7b30-49bb-a375-335e90e40bfc
caps.latest.revision: 8
---
# Building the TPs (CPI-C)
The Common Programming Interface for Communications (CPI-C) samples are designed to be built using the command-line compiler or the IDE in Microsoft Visual Studio.  
  
 To build the CPI-C samples installed with Host Integration Server, set the following environment variables listed in the following table.  
  
|Variable|Description|  
|--------------|-----------------|  
|ISVLIBS|The directory containing the Host Integration Server LIB files for Windows Server.|  
|ISVINCS|The directory containing the Host Integration Server header files.|  
|SAMPLEROOT|The root directory where the sample code provided as part of the SDK has been installed on a local hard disk.|  
  
 For example, if you installed the Host Integration Server SDK directory to the default location (C:\Program Files\Microsoft Host Integration Server 2010\SDK), use the following lines to set the variables (assumes Intel binaries are being produced for Windows Server.  
  
```  
ISVLIBS=C:\Program Files\Microsoft Host Integration Server 2010\SDK\LIB  
ISVINCS=C:\Program Files\Microsoft Host Integration Server 2010\SDK\Include  
SAMPLEROOT=C:\Program Files\Microsoft Host Integration Server 2010\SDK\Samples\SNA  
```  
  
 To build a specific sample (APING, for example) using Visual Studio, open the appropriate Microsoft Visual C++ project file (SNA\aping\aping.vcproj, for example) from the **File** menu. Select a configuration and build the sample from the **Build** menu. Each project file has two configurations, one for a DEBUG build and one for a RETAIL build.  
  
## See Also  
 [CPI-C Samples](../HIS2010/cpi-c-samples.md)