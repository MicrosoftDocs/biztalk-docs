---
title: "Non-APPC LU Status1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ca97bcb-38ff-44ff-b77a-30815dd17a92
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Non-APPC LU Status
The status of a non-Advanced Program-to-Program Communications (APPC) logical unit (LU) can be:  
  
- Inactive  
  
- In Session  
  
- System Services Control Point (SSCP). This indicates that the LU is in use, but is not yet bound to a specific host application.  
  
- Available: Indicates the LU is recognized by the host as an available LU.  
  
- Pending: Indicates that a user is trying to access the LU, but either the connection is inactive or the mainframe does not recognize the LU.  
  
- Unavailable: Applies to downstream LUs only.  
  
  To view the status of an LU, select the LU in the SNA Manager.  
  
## See Also  
 [Host Integration Server Status](../core/host-integration-server-status1.md)