---
title: "Included Files2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 206b8454-9b3e-460a-9bed-cb37cbcff25f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Included Files
To compile a SNALink, the header files SNA_DLC.H, SNA_CNST.H and TRACE.H are required. In addition, one of the standard operating system header files may be required. To include the required files, the following lines should be used in your application:  
  
```  
#include <sna_dlc.h>  
#include <sna_cnst.h>  
#include <trace.h>  
```  
  
> [!NOTE]
>  The TRACE.H include file is required to enable SNA tracing and use of the [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] Trace viewer utility.