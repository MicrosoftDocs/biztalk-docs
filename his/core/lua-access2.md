---
title: Logical unit application (LUA) access
description: Learn about LUA access so you can write customized applications to communicate with the host.
ms.service: host-integration-server
ms.topic: article
ms.date: 11/30/2017
---

# Logical unit application (LUA) access for host communication

A LUA is an application programming interface (API) that allows you to write customized applications to communicate with the host. LUA logical units (LUs) enable programmable control over the SNA messages that are sent between the communications software and the host. You can use LUA LUs to communicate with LU types 0, 1, 2, or 3 at the host as long as the application sends the appropriate SNA messages required by the host.
  
A LUA uses a local LU, which uses Host Integration Server to communicate with the host system. When Host Integration Server connects to the host, there are three progressive sessions:

- The PU-SSCP between the Host Integration Server physical unit (PU) and the system services control point (SSCP) on the host.

- The SSCP-LU session between the LUA LU at the computer running the application and the SSCP.

- The LU-LU session between the LUA LU at the computer running the application and the host LU.

The LU session's normal flow carries most of the data. The other flows are used only for control purposes.  
  
The Host Integration Server configuration file contains information that's required for LUA applications to communicate. You configure a LUA LU to use a connection to the host by the installed link service. It is then given the LU number that matches that of an LU on the host.  

The configuration might include LUA LU pools. A pool is a group of LUs with similar characteristics that allows an application to use any free LU from the pool. You can use this capability to allocate LUs on a first-come, first-served basis when there are more applications than LUs available, or to provide a choice of LUs on different connections, as well as [providing hot backup and load balancing](providing-hot-backup-and-load-balancing-3270-1.md).  

The following lists describes the communications components to configure:

- A link service for communicating with the host
- A connection to the host that uses the link service
- A Host Integration Server service that owns the connection. This component is automatically configured.
- A LUA LU on a Host Integration Server service, configured to use the connections, with an LU number that matches an LU on the host

You can perform the following actions with LUA LUs:

- Assign an LUA LU, or a range of LUA LUs, to a connection.

  A range of LUA LUs allow multiple applications to simultaneously use LUAs. Configure the numbering for a new range of LUA LUs by specifying the lowest LU number and the number of LUs in the range. After you create a range of LUs, you can change the numbering of individual LUs in the range.

- Configure properties for a new LUA LU or a new range of LUA LUs. This configuration includes specifying the LU name and LU number for the LUs.  

- Group LUA LUs into one or more LUA LU pools. A LUA LU pool contains a number of LUs that are made available as a group to LUA applications. A given application can get LU access as long as one of the pooled LUs is available.

- View or modify an existing LUA LU, regardless of whether that LU was created as part of a range.

- Copy properties from one LU to another.

- Move a LU or LUA LU from one connection to another.

  - To determine the appropriate names and numbers for LUA LUs on your system, check with the host administrator.

  - If the number you specify has already been assigned to an LU or an APPC LU-LU pair on the current connection, you must use a different number. The range for LU numbers is from 1 through 254.

  - The LU name can't be the same as any other LU name or pool name, except for APPC LU names, on the server.

  - If the High Priority LU is assigned to a pool, the priority setting of the pool overwrites the setting of the LU.

- Delete a LU.

## See also  

[Precedence of Accounts in Determining LU Access](precedence-of-accounts-in-determining-lu-access1.md)    
[Host Integration Server 3270 Connectivity](host-integration-server-3270-connectivity2.md)    
