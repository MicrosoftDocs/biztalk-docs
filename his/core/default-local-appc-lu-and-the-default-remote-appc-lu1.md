---
title: "Default Local APPC LU and the Default Remote APPC LU1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec30bdb6-838e-4639-b0b1-40db662955f3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Default Local APPC LU and the Default Remote APPC LU
If a user or group uses transaction programs, 5250 emulators, or APPC applications, you can assign a default local APPC LU and a default remote APPC LU. These default LUs are accessed when the user or group member starts an APPC program (a TP, 5250 emulator, or APPC application) and the program does not specify LU aliases.  
  
 With Host Integration Server, you can assign a default local APPC LU and a default remote APPC LU to each user or group. A user or group member can then start APPC programs (TPs, 5250 emulators, or APPC applications) that do not specify LU aliases. Host Integration Server will use the default local APPC LU and the default remote APPC LU assigned to that user or group.  
  
 There are two steps before assigning default APPC LUs to a user or group:  
  
1. The user or group must have an account on the local area network.  
  
2. The user or group must be added to the list used by Host Integration Server.  
  
   If a user is assigned LUs through one or more accounts, such as group accounts and the user's individual account, one account determines the access for that user. The account that determines this access is the account found first when searching is performed in this order:  
  
- User accounts (highest priority)  
  
- Domain groups  
  
- Local groups  
  
- Well-known groups such as Everyone (lowest priority)  
  
  For example, suppose a user account (a high-priority account) called JOHND contains LOCLU1 as the default local APPC LU, but no default remote APPC LU. At the same time, suppose a local group (a low-priority account) of which JOHND is a member contains LOCLU2 as the default local APPC LU, and REMLU2 as the default remote APPC LU. For JOHND, the high-priority assignment, the default local APPC LU of LOCLU1 will be combined with the only other available assignment, the default remote APPC LU of REMLU2.  
  
## See Also  
 [APPC Mode Definition](../core/appc-mode-definition2.md)   
 [Implicit Incoming Remote LU and Implicit Incoming Mode](../core/implicit-incoming-remote-lu-and-implicit-incoming-mode1.md)   
 [Default Outgoing Local APPC LU Pool](../core/default-outgoing-local-appc-lu-pool1.md)   
 [Single-System APPC](../core/single-system-appc2.md)