---
title: "Building the LUA Samples | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8cb67cd9-c93a-4646-b623-244040246959
caps.latest.revision: 6
---
# Building the LUA Samples
The logical unit application (LUA) samples are designed to be built using Visual C++ 6.0 or later using the command-line compiler, or using Visual Studio.  
  
 To build the LUA samples, set the environment variables listed in the following table.  
  
|Variable|Description|  
|--------------|-----------------|  
|ISVLIBS|The directory containing the [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] LIB files for<br /><br /> Windows Server.|  
|ISVINCS|The directory containing the [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] header files.|  
|SAMPLEROOT|The root directory where the sample code provided as part of the software development kit (SDK) has been installed on a local hard disk.|  
  
 For example, if you installed the Host Integration Server SDK directory to the default location (C:\Program Files\Microsoft Host Integration Server 2010\SDK), use the following lines to set the variables (assumes Intel binaries are being produced for Windows Server):  
  
```  
ISVLIBS=C:\Program Files\Microsoft Host Integration Server 2010 \SDK\LIB  
ISVINCS=C:\Program Files\Microsoft Host Integration Server 2010\SDK\Include  
SAMPLEROOT=C:\Program Files\Microsoft Host Integration Server 2010\SDK\Samples\SNA  
```  
  
 To build a specific sample (the Win32 version of RUI3270, for example) using Visual Studio, open the appropriate Visual C++ project file (SNA\RUI3270\Win32\NRUI3270.vcproj, for example) from the **File** menu. Select a configuration and build the sample from the **Build** menu. Each project file has two configurations, one for a DEBUG build and one for a RETAIL build.  
  
## See Also  
 [LUA Samples](../HIS2010/lua-samples.md)