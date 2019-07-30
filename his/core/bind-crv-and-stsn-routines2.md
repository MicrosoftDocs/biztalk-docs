---
title: "BIND, CRV, and STSN Routines2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a67db8b-de29-4e5e-a41e-77d740b671bb
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# BIND, CRV, and STSN Routines
For BIND and STSN routines supplied by the application, the names of dynamic-link libraries (DLLs) and the entry points for procedures are passed in the [SLI_OPEN](../core/sli-open2.md) verbs verb control block (VCB). During **SLI_OPEN**, the BIND and STSN routines are called if the appropriate SNA request is received. When a BIND routine is not supplied by the application, the Session Level Interface (SLI) performs a minimal check of the BIND commands and responds as necessary. If no STSN routine is supplied and an STSN request arrives, a positive response is issued by the SLI. If a CRV request arrives, a negative response is issued by the SLI.  
  
 Names for BIND and STSN routines are provided as extensions of the SLI_OPEN verbs VCB. The lua_extension_list_offset parameter provides the offset from the start of the VCB to the first name in the extension list.  
  
 The function prototype for a user-defined BIND or STSN routine on Windows Server is as follows:  
  
## Syntax  
  
```  
  
lpVcb  
  
```  
  
## Remarks  
 The *lpVcb* parameter is a pointer to a logical unit application (LUA) VCB.