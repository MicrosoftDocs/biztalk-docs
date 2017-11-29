---
title: "Path Errors (Category X&#39;80&#39;)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61247bf0-3fde-40b0-9321-cf446f539b5d
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Path Errors (Category X&#39;80&#39;)
Sense codes in this category indicate that the request could not be delivered to the required half-session because of path errors. The following codes are in this category.  
  
|Code|Meaning|  
|----------|-------------|  
|8004|Unrecognized destination field address (DAF)|  
|8005|No session|  
|8006|Invalid format identification (FID): Error detected and logged; negative response not sent|  
|8007|Segmentation error request/response header (RH) not present or too short: negative response sent only for segmentation error|  
|8008|Primary unit (PU) not active: SSCP-PU was not active and request was not ACTPU or DACTPU|  
|8009|Logical unit (LU) not active: DAF specified an LU for which the SSCP-SLU session has not been activated, and request was not ACTLU or DACTLU|  
|800F|Invalid address combination|  
  
## See Also  
 [SNA Sense Codes](../core/sna-sense-codes.md)