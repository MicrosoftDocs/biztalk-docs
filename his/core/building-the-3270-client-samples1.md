---
description: "Learn more about: Building the 3270 Client Samples"
title: "Building the 3270 Client Samples1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2b62a8a-487d-4af4-af02-15d1677d179e
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Building the 3270 Client Samples
When you install Host Integration Server, all the 3270 client samples are built in a similar way, as described in this section. First, set the environment variables listed in the following table.  
  
|Variable|Description|  
|--------------|-----------------|  
|ISVLIBS|The directory containing the Host Integration Server LIB files for Microsoft Windows.|  
|ISVINCS|The directory containing the Host Integration Server header files.|  
|SAMPLEROOT|The root directory where the sample code provided as part of the SDK has been installed on a local hard disk.|  
  
 For example, after you copy the contents of the SDK  to C:\SNASDK, use the following lines to set the variables:  
  
```  
ISVLIBS=C:\SNASDK\Lib  
ISVINCS=C:\ SNASDK\Include  
SAMPLEROOT=C:\SNASDK\Samples\SNA  
```  
  
 Next, run NMAKE on the .mak file in each subdirectory below this root directory containing the actual sample source code. For example, for APING and APINGD, change to the Samples\aping directory and type the following:  
  
 **nmake -f makeping.mak**
