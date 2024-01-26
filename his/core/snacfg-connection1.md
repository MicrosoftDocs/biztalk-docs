---
description: "Learn more about: Snacfg Connection"
title: "Snacfg Connection1"
ms.custom: ""
ms.date: "12/14/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Snacfg Connection

## Purpose
  
 Allows you to view, add, delete, or modify connections, including peer connections (necessary for APPC LUs).  
  
 Before configuring a connection, you must configure the server and link service that the connection will use.  
  
> [!NOTE]
> Configuration settings specified with snacfg connection correspond to connection settings configured with the SNA Manager.  
  
## Syntax  
  
```  
 
SNACFG [configpath] CONNECTION /LIST
SNACFG [configpath] CONNECTION connectionname
SNACFG [configpath] CONNECTION connectionname /PRINT
SNACFG [configpath] CONNECTION connectionname /ADD [options]
SNACFG [configpath] CONNECTION connectionname [options]
SNACFG [configpath] CONNECTION connectionname /DELETE

```  

 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/LIST**  
 Generates a list of configured connections.  
  
 *connectionname*  
 Specifies a name for the connection to be configured or viewed. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. A new connection name cannot be the same as any other connection name in the installation, and cannot be the reserved name SNASERVR.  
  
 If no options are specified after *connectionname*, the command-line interface displays a list of the configuration settings for the specified connection.  
  
 **/ADD**  
 Adds a connection called *connectionname*. To configure the connection, either specify other options after **/add**, or specify configuration options in additional **snacfg connection** commands (using the same *connectionname*).  
  
 **/DELETE**  
 Deletes *connectionname*.  
  
## Options Used with All Connection Types

 **/server:** *servername*  
 Specifies the server to which to assign or move the connection. When **/add** is used, this option is required. The server name should be in the format machine_name or \\\machine_name\snaservr (for specifying the primary node on the machine) and \\\machine_name\snasrv02 (or snasrv03, snasrv04, and so on) for specifying the secondary nodes on the machine.  
  
 **/conntype:{ IP-DLC }**  
 Specifies the connection type. When **/add** is used, this option is required.  
  
 **/comment:**" *text*"  
 Adds an optional comment for the specified connection. The comment can contain as many as 25 characters; enclose the comment in quotes.  
  
 **/linkservice:** *linkname*  
 Specifies the name of the link service to be used by *connectionname*. The link service type must match the connection type, or the **snacfg** command will not run.  
  
 In order for the link service to function correctly, it must be installed with the SNA Manager. Link services can also be installed with **snacfg link**; however, the SNA Manager is the recommended interface for installing link services, because it helps ensure that the resulting configuration is functional.  
  
 **/activation:{ onserverstartup &#124; ondemand &#124; byadministrator }**  
 For outgoing calls on *connectionname*, tells how the connection will be activated: on server startup, on demand, or by the administrator. (For incoming calls, activation is irrelevant, since the connection always begins listening for calls on server startup.)  
  
 If no value has been specified for **/activation**, the default is **ondemand**.  
  
 **/localblockno:** *hexdigits*  
 Specifies the local block number, a three-digit hexadecimal number. The local block number forms the first part of the Local Node ID, an eight-digit hexadecimal number that identifies the local system.  
  
 Do not use 000 or FFF for the local block number. These values are reserved.  
  
 For connections to host systems, the local block number should match IDBLK in VTAM.  
  
 **/localnodeno:** *hexdigits*  
 Specifies the local node number, a five-digit hexadecimal number. The local node number forms the last part of the Local Node ID, an eight-digit hexadecimal number that identifies the local system.  
  
 For connections to host systems, the local node number should match IDNUM in VTAM.  
  
 **/cpname:** *text*  
 Specifies the control point name of the remote node, as it is represented in Format 3 XIDs. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @.  
  
 The control point name of the remote node works together with **netname**. If either of these parameters is supplied, the other should also be supplied.  
  
 When connecting to a host system and using a remote control point name, the name should match the SSCPNAME parameter in the VTAM Start command for the remote SSCP (the VTAM system).  
  
 **/netname:** *text*  
 Specifies the name of the network for the remote node, as it is represented in Format 3 XIDs. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @.  
  
 The **netname** parameter works together with the control point name of the remote node. If either of these parameters is supplied, the other should also be supplied.  
  
 **/remoteblockno:** *hexdigits*  
 Specifies the remote block number, a three-digit hexadecimal number. The remote block number forms the first part of the Remote Node ID, an eight-digit hexadecimal number that identifies the remote system.  
  
 Do not use 000 or FFF for the remote block number. These values are reserved.  
  
 **/remoteend:{ Host &#124; Peer}**  
 Specifies whether the connection is to be a host or peer.  
  
 **/remotenodeno:** *hexdigits*  
 Specifies the remote node number, a five-digit hexadecimal number. The remote node number forms the last part of the Remote Node ID, an eight-digit hexadecimal number that identifies the remote system.  
  
 **/xidtype:{ format0 &#124; format3 }**  
 Specifies the XID type, the type of identifying information for [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] to send. The choices are **format0** (Format 0) and **format3** (Format 3). Format 0 sends only the Node ID. Format 3 sends up to 100 bytes of identifying information, including the local node ID and control point name.  
  
 If no XID type has been specified, the default is **format3**.  
  
 **/calldirection:{ Incoming** &#124;  **Outgoing** &#124;  **Both }**  
 This option specifies the call direction.  

 **/localcpname:** *text*  
 The Local Control Point Name works with the Network Name to identify a system. The maximum length is eight characters.  
  
 **/localnetname:** *text*  
 The Local Network Name works with the Local Control Point Name to identify a system. The maximum length is eight characters.  
  
 **/compression:{ None &#124; RLE &#124; LZ9 }**  
 These options offer progressively better compression, but at a progressively higher CPU usage cost.  
  
 **/peerdlcrole:{ Primary &#124; Secondary &#124; Negotiable }**  
 Specifies the role used in peer-to-peer communications.  
  
 **/dynamicludef:{ yes &#124; no }**  
 Specifies that this connection supports dynamic remote APPC LU allocation.  
  
## See Also

 [Snacfg Reference](../core/snacfg-reference2.md)
