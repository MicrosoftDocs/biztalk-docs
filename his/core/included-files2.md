---
description: "Learn more about: Included Files"
title: "Included Files2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Included Files
To compile a SNALink, the header files SNA_DLC.H, SNA_CNST.H and TRACE.H are required. In addition, one of the standard operating system header files may be required. To include the required files, the following lines should be used in your application:  
  
```  
#include <sna_dlc.h>  
#include <sna_cnst.h>  
#include <trace.h>  
```  
  
> [!NOTE]
>  The TRACE.H include file is required to enable SNA tracing and use of the Host Integration Server Trace viewer utility.
