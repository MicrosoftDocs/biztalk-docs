---
title: "Compiler Options1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20704965-e497-4296-82fb-007fea14409c
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Compiler Options
When compiling the SNALink DLL, the following compiler options are required:  
  
|Option|Explanation|  
|------------|-----------------|  
|/c|Compile only, without linking. Linking is done as a separate phase to include the required Microsoft [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] libraries.|  
|/D NOTRC|The NOTRC macro specifies that internal tracing should not be compiled into the application.<br /><br /> The /D NOTRC option should be used for building a final system (internal tracing should not be included because it will degrade performance and occupancy). For a development system, you may want to compile with internal tracing; if so, remove the /D NOTRC option.|  
|/D WIN32_SUPPORT|The macro WIN32_SUPPORT is used in the header files SNA_DLC.H, SNA_CNST.H, and TRACE.H to support variants of the DLC interface for Microsoft Windows.|  
|/Gzs|**z**: Use stdcall conventions .**s**: Remove stack check calls.|  
  
 The following compiler flags are required, but any of the valid options for each flag may be used, as appropriate to your application:  
  
|||  
|-|-|  
|/O|Optimization|  
|/W|Warning level|