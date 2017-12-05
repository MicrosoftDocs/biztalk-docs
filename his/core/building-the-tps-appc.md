---
title: "Building the TPs (APPC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 122ffa60-cfd2-41ab-bd31-1ab2e6a88c72
caps.latest.revision: 8
---
# Building the TPs (APPC)
The APPC samples are designed to be built by using the command-line compiler or the interactive development environment (IDE) in Microsoft Visual Studio.  
  
 To build the APPC samples installed with Host Integration Server, set the following environment variables:  
  
|Variable|Specifies|  
|--------------|---------------|  
|ISVLIBS|Directory containing the Microsoft Host Integration Server LIB files for Microsoft Windows|  
|ISVINCS|Directory containing the WINSNA header files|  
|SAMPLEROOT|Root directory of the sample code|  
  
 For example, if you installed the Host Integration Server SDK directory to the default location (C:\Program Files\Microsoft Host Integration Server 2010\SDK), use the following lines to set the variables (assuming that Intel binaries are being produced for Windows):  
  
```  
ISVLIBS=C:\Program Files\Microsoft Host Integration Server 2010\SDK\LIB  
ISVINCS=C:\Program Files\ Microsoft Host Integration Server \SDK\Include  
SAMPLEROOT=C:\Program Files\ Microsoft Host Integration Server \SDK\Samples\SNA  
  
```  
  
 To build a specific sample (SendTp, for example) using the Visual Studio IDE, start Visual Studio and open the appropriate Microsoft Visual C++ project file (NetworkIntegration\appc\sendtp.vcproj, for example) from the **File** menu. Select a configuration and build the sample from the **Build** menu. Each Visual C++ project file has two configurations, one for a DEBUG build and one for a RETAIL build.  
  
## See Also  
 [APPC Samples](../core/appc-samples.md)