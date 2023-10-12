---
description: "Learn more about: Default LUs"
title: "Default LUs2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Default LUs
Any LU can be configured to be in a pool of default local LUs available for use by invoking transaction programs (TPs).  
  
 For a user or group who will be using TPs, 5250 emulators, and/or APPC applications, you can assign a default local APPC LU and a default remote APPC LU. If the invoking TP specifies the LU alias that it uses (in [TP_STARTED](../core/tp-started2.md)), that LU alias must match a local APPC LU alias on the supporting SNA server. If the invoking TP leaves the LU alias blank in **TP_STARTED**, one of two methods for designating a default LU must be carried out on the supporting SNA server:  
  
-   Assign a default local APPC LU to the user or group that starts the invoking TP (that is, the user or group logged on at the system from which **TP_STARTED** is issued).  
  
     **—or—**  
  
-   Designate one or more LUs as members of the default outgoing local APPC LU pool. The SNA server first attempts to determine the default local APPC LU of the associated user or group, then attempts to assign an available LU from the default outgoing local APPC LU pool; if these attempts fail, the SNA server rejects the request.  
  
## AS/400 Environment  
 In AS/400 environments, the ability to assign default APPC LUs to users or groups is especially useful because it gives the administrator centralized control over these LU assignments. In such environments, for each user or group, assign both a default local APPC LU and a default remote APPC LU. Assigning a default local APPC LU for each user fulfills the normal AS/400 procedure of assigning local LUs on a per-user basis. Assigning a default remote APPC LU is equivalent to assigning a default AS/400 for the user to connect to, since the remote LU designates the AS/400. By making these assignments, the administrator can centrally control the default AS/400 that a 5250 emulator user connects to.  
  
## See Also  
 [TP_STARTED](../core/tp-started2.md)
