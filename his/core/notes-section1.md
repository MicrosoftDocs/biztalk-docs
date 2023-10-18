---
description: "Learn more about: Notes Section"
title: "Notes Section1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 95611c38-7ebd-4e04-a154-700fcbfc2df7
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Notes Section
This section contains notes about AS/400 computers and local and remote names.  
  
## Note About AS/400 Computers  
 To connect to an AS/400 computer, supply both local node and remote node parameters for the Network Name and the Control Point Name. These properties are configured in separate dialog boxes:  
  
- **Local node (server) properties.** In the **Server Properties** dialog box of the computer running Host Integration Server, type the **Control Point Name** and the **Network Name**. The server Network Name must correspond to the RMTNETID parameter in the AS/400 APPC controller description. (The default for the AS/400 computer network ID is typically APPN.) If this value is set to **\*SAME**, refer to the Local Network ID parameter in the AS/400 Network Attributes screen (using the **dspneta** command). The server Control Point Name must match the RMTCPNAME parameter in the AS/400 APPC controller description.  
  
   If you specify a CPNAME in **Connection Properties**, it overrides the CPNAME in the **Server Properties** dialog box. The CPNAME in **Server Properties** is the default and will be used unless it is changed in **Connections Properties**.  
  
- **Remote node (connection) properties.** In the **Properties** dialog box for an IP-DLC connection, type the **Network Name** and **Control Point Name (CP name)** of the AS/400 computer into the **Network Name (Remote Node)** and **Control Point Name (Remote Node)** fields. The AS/400 Network Name and Local Control Point Name can be found on the AS/400 Network Attributes screen using the DSPNETA. For more information about these fields, click Help on the **Properties** dialog box for the connection.  
  
   On an AS/400 computer, the Network Name is specified in the Local network ID parameter in the Network Attributes screen and in the RMTNETID parameter on the APPC controller description. For more information, see your APPN documentation.  
  
## Using Remote Node Identifiers  
 You can use several types of parameters to specify the remote node with which a connection should connect:  
  
## Network Name (Remote Node) and Control Point Name (Remote Node)  
 As a general guideline, use these parameters if the administrator of the remote host, peer, or downstream system uses them.  
  
 These two parameters work together; if either parameter is supplied, the other should also be supplied. These parameters are used only for Format 3 exchange identifications (XIDs), one of two types of exchange identification. Format 3 XIDs are generally used for APPC. If a connection does not use Format 3 XIDs, there is no need to specify these parameters.  
  
## Remote Node ID  
 As a general guideline, use this parameter if the administrator of the remote host, peer, or downstream system uses it. This parameter can be used in Format 0 XIDs or Format 3 XIDs, the two types of identification exchange. **Format 0 XID**s are generally used for 3270 communication and for LUA; **Format 3 XID**s are generally used for APPC.  
  
## Note About Local and Remote Names  
 The **Network Name** and **Control Point Name** for the remote node are different from the **Network Name** and **Control Point Name** for the local node. The remote **Network Name** and **Control Point Name** are specified in the **Connection Properties** dialog box. The local **Network Name** and **Control Point Name** are specified in the **Server Properties** dialog box.  
  
## Primary Configuration Server  
 The primary configuration server is the Host Integration Server computer designated to contain the domain-wide configuration file. The configuration file reflects the Host Integration Server resources for the SNA subdomain, including all Host Integration Server computers, link services, LUs, 3270 users, and so on. There can be only one primary server in the subdomain.  
  
## Backup Configuration Server  
 The backup configuration server is a Host Integration Server computer on which the configuration file is replicated by Host Integration Server. There can be more than one backup server in an SNA subdomain. Host Integration Server will load the copy of the configuration file located on a backup Host Integration Server computer if the primary Host Integration Server computer goes down. In this case, servers and connections can be started and stopped, but the configuration cannot be changed or saved.  
  
## Identifiers in Incoming XIDs  
 When deciding which type of remote node identifier to specify for a connection that accepts incoming calls, it may be helpful to understand how Host Integration Server uses exchange identifications (XIDs) from incoming calls.  
  
 When Host Integration Server receives an XID from an incoming call, it looks at the XID for some type of identifier of the remote system that made the call. It compares this identifier, in the order shown in the following list, against identifiers stored in the Host Integration Server configuration. If it finds a match, it accepts the call. If it finds that identifiers are left unspecified (in the configuration or the XID), and the connection is an SDLC connection, Host Integration Server accepts the call, pending further exchange of information.  
  
 Identifiers are compared in the following order:  
  
1.  If the incoming XID is Format 3, Host Integration Server examines the XID for a remote node Network Name and Control Point Name. If these parameters are present in both the Incoming XID and in the Host Integration Server configuration, and they match, the call is accepted. If the parameters are present and do not match, the call is rejected.  
  
2.  If the parameters were not available for the preceding step, Remote Node IDs are examined next. (Remote Node IDs may be used in either Format 0 or Format 3 XIDs.) If a Remote Node ID is present in both the Incoming XID and in the Host Integration Server configuration, and they match, the call is accepted. If the parameters are present and do not match, the call is rejected.  
    
## See Also  
 [Understanding Connectivity](../core/understanding-connectivity1.md)
