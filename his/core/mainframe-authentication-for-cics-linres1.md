---
description: "Learn more about: Mainframe Authentication for CICS LINREs"
title: "Mainframe Authentication for CICS LINREs1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Mainframe Authentication for CICS LINREs
If you use a CICS LINK LU 6.2 remote environment (RE), you must use resource-level authentication.  
  
 Because of a restriction imposed by the IBM Distributed Program Link (DPL) protocol, a user ID and password transmitted from the workstation by Transaction Integrator (TI) are ignored and not used for transaction-level authentication. The target CICS region expects, under the circumstances, that authentication was completed by the TI application that initiates the IBM DPL call. (Traditionally, the application that initiates an IBM DPL call is a program in another CICS region.) Instead of using credentials from the FMH-5 ATTACH, for transaction-level authentication, the target CICS region associates the default user ID for the region with the transaction ID of the CICS task (the mirror transaction).  
  
 As a result of this behavior, any attempt to secure the mirror transaction can cause an application malfunction because of a failure to authenticate.  
  
## See Also  
 [Security Implications](../core/security-implications1.md)
