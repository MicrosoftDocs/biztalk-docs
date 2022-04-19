---
description: "Learn more about: Mainframe Authentication for CICS LINK"
title: "Mainframe Authentication for CICS LINK1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec919c4d-b7f8-45d6-a9d2-f990689208c7
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Mainframe Authentication for CICS LINK
Resource-level authentication is recommended in the CICS region. Due to a restriction imposed by the IBM Distributed Program Link (DPL) protocol, a user ID and password transmitted from the workstation by TI are ignored and not used for transaction-level authentication. The target CICS region expects, under the circumstances, that authentication has been completed by the application that executes the IBM DPL; for example, a TI application on the PC. (Traditionally, the application that executes an IBM DPL has been another CICS region.) Instead, for transaction-level authentication, the target CICS region associates the default user ID for the region with the transaction ID of the CICS (mirror transaction) task and the user ID from the sender is ignored. Unless this is taken into consideration, attempts to secure the mirror transaction can cause an application malfunction because of the failure to authenticate.  
  
## See Also  
 [Application Integration (Security)](../core/application-integration-security-2.md)
