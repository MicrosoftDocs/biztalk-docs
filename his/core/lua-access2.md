---
title: "LUA Access2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11bc6bb3-d539-421a-9ef6-2ea6bab05de8
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# LUA Access
Logical unit application (LUA) is an application programming interface (API) that allows you to write customized applications to communicate with the host. LUA LUs enable programmable control over the SNA messages that are sent between the communications software and the host. LUA LUs can be used to communicate with LU types 0, 1, 2, or 3 at the host as long as the application sends the appropriate SNA messages required by the host.  
  
 An LUA application uses a local LU, which uses Host Integration Server to communicate with the host system. When Host Integration Server connects to the host, there are three progressive sessions:  
  
1. The PU-SSCP between the Host Integration Server physical unit (PU) and the system services control point (SSCP) on the host.  
  
2. The SSCP-LU session between the LUA LU at the computer running the application and the SSCP.  
  
3. The LU-LU session between the LUA LU at the computer running the application and the host LU.  
  
   The LU session's normal flow carries most of the data. The other flows are used only for control purposes.  
  
   The Host Integration Server configuration file contains information that is required for LUA applications to communicate. An LUA LU is configured to use a connection to the host by the link service that is installed. It is then given the LU number that matches that of an LU on the host.  
  
   The configuration may include LUA LU pools. A pool is a group of LUs with similar characteristics, and it allows an application to use any free LU from the pool. This feature can be used for allocating LUs on a first-come, first-served basis when there are more applications than LUs available, or for providing a choice of LUs on different connections, as well as [providing hot backup and load balancing](../core/providing-hot-backup-and-load-balancing-3270-1.md).  
  
   The communications components to be configured include:  
  
- A link service for communicating with the host.  
  
- A connection to the host that uses the link service.  
  
- A Host Integration Server service which owns the connection. This component is configured automatically.  
  
- An LUA LU on a Host Integration Server service, configured to use the connections, with an LU number that matches an LU on the host.  
  
  You can perform the following actions with LUA LUs:  
  
- Assign an LUA LU, or a range of LUA LUs, to a connection. A range of LUA LUs will allow multiple applications to use LUAs simultaneously. Configure the numbering for a new range of LUA LUs by specifying the lowest LU number and the number of LUs in the range.  
  
   After creating a range of LUs, you can change the numbering of individual LUs in the range.  
  
- Configure properties for a new LUA LU or a new range of LUA LUs. This includes specifying the LU name and LU number for the LUs.  
  
- Group LUA LUs into one or more LUA LU pools. An LUA LU pool contains a number of LUs that are made available as a group to LUA applications. A given application can get LU access as long as one of the pooled LUs is available.  
  
- View or modify an existing LUA LU, regardless of whether it was created as part of a range.  
  
- Copy properties from one LU to another.  
  
- Move an LU from one connection to another.  
  
- Delete an LU.  
  
- Move an LUA LU from one connection to another.  
  
  Check with the host administrator to determine the appropriate names and numbers for LUA LUs on your system. The LU Number for LUs on 802.2 or Synchronous Data Link Control (SDLC) connections should match the LOCADDR= parameter of the LU definition in VTAM or in the NCP Gen.  
  
  If the number you specify has already been assigned to an LU or an APPC LU-LU pair on the current connection, you must use a different number. The range for LU numbers is from 1 through 254.  
  
  The LU Name cannot be the same as any other LU name or pool name (except for APPC LU names) on the server.  
  
  If the High Priority LU is assigned to a pool, the priority setting of the pool overwrites the setting of the LU.  
  
  On an 802.2 or SDLC connection, you can configure multiple LUs at one time by configuring them as a consecutively numbered range. Multiple LUA LUs will allow multiple applications to access the host simultaneously. After configuring the range of LUs, you can modify the numbering and properties of individual LUs in the range.  
  
## See Also  
 [Precedence of Accounts in Determining LU Access](../core/precedence-of-accounts-in-determining-lu-access1.md)   
 [Downstream Connections (3270)](../core/downstream-connections-3270-2.md)   
 [Host Integration Server 3270 Connectivity](../core/host-integration-server-3270-connectivity2.md)