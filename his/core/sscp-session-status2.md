---
title: "SSCP Session Status2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56dbec2f-aad8-4a81-a2f3-68bb917433a1
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SSCP Session Status
While the system services control point (SSCP) connection is open, the local node reports the initial state and any subsequent changes of state of the SSCP session to the application using [Status-Session](./status-session2.md) messages. There are four distinct **Status-Session** status codes that can occur for the SSCP connection:  
  
- **No-Session.** The SSCP session between the SNA server logical unit (LU) and the host SSCP is not active because the SNA server physical unit (PU) or LU is not activated. The **Status-Session** carries a qualifying status code to indicate why the SSCP session is inactive. The application cannot use the SSCP connection to send data to the host SSCP. The qualifiers are:  
  
  -   **PU-INACTIVE.** Activate PU (ACTPU) has not been received or Deactivate PU (DACTPU) has been received.  
  
  -   **PU-ACTIVE.** ACTPU(COLD) has been received from the SSCP.  
  
  -   **PU-REACTIVATED.** ACTPU(COLD) has been received while the PU was active. (The application is not informed if ACTPU(ERP) is received while the PU is active.)  
  
  -   **LU-INACTIVE.** ACTLU has not been received, or DACTLU has been received.  
  
- **Link-Error.** The SSCP session between the SNA server LU and the host SSCP is not active, due to a data link control (DLC) error. The **Status-Session** carries a qualifying status code that gives the error code reported by the DLC. The application cannot use the SSCP connection to send data to the host SSCP.  
  
   Note that this session state is reported when the local node is informed that the locality containing the Host Integration Server Synchronous Data Link Control (SDLC) link service has been lost due to a path failure. The qualifier 0x0D is used. The link service will close the link when it is informed of the path error so the application can treat this as an outage.  
  
- **LU-Active.** The SSCP session is active due to the receipt of ACTLU. The application can use the SSCP connection to send data to the host SSCP.  
  
- **LU-Reactivated.** The SSCP session has been reactivated due to the receipt of an ACTLU from the host SSCP. The SSCP connection is still active, but data may have been lost.  
  
  For more information, see [Status-Session Codes](../core/status-session-codes1.md).