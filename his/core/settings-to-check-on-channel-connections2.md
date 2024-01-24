---
description: "Learn more about: Settings to Check on Channel Connections"
title: "Settings to Check on Channel Connections2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Settings to Check on Channel Connections
The number of parameters involved in channel connections is fewer than with other types of connections. The key parameters to note are those specifying addresses and, for channel connections, the Max BTU Length.  
  
 If one or more 3270 LUs never becomes active, even when users are attempting to start sessions, the LOCADDR settings in the LU definitions in VTAM or NCP may not match the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] LU numbers, or some or all of the LUs may be inactivated in VTAM or NCP. To correct this, consult with the administrator of the host system.
