---
title: Notes about IBM System i computers
description: Learn more about IBM System i computers along with local and remote names.
ms.service: host-integration-server
ms.topic: conceptual
ms.date: 11/30/2017
---

# Notes about IBM System i computers plus local and remote names

The following guide provides more information about IBM System i computers along with local and remote names.

## IBM System i Computers

To connect to an IBM System i computer, supply both local node and remote node parameters for the **Network Name** and the **Control Point Name** properties. You can configure these properties in the following individual boxes:  
  
- **Local node (server) properties**

  On the computer running Host Integration Server (HIS), in the **Server Properties** box, type the **Control Point Name** and the **Network Name**.

  The server's network name must correspond to the RMTNETID parameter in the IBM System i APPC controller description. The default value for the IBM System i computer network ID is typically **APPN**. If this value is set to **\*SAME**, refer to the Local Network ID parameter in the **IBM System i Network Attributes** screen, which you can view using the **dspneta** command. The server Control Point Name must match the RMTCPNAME parameter in the IBM System i APPC controller description.  
  
   If you specify a CPNAME in **Connection Properties**, this value overrides the CPNAME in the **Server Properties** box. The CPNAME in **Server Properties** is the default value and is used unless changed in **Connections Properties**.  
  
- **Remote node (connection) properties**

  In the **Properties** box for an IP-DLC connection, for the **Network Name (Remote Node)** and **Control Point Name (Remote Node)** fields, type the **Network Name** and **Control Point Name (CP name)** of the IBM System i computer.

  You can find the IBM System i **Network Name** and **Local Control Point Name** on the IBM System i Network Attributes screen, which you can view using the **DSPNETA** command. For more information about these fields, on the connection's **Properties** box, select **Help**.

  On an IBM System i computer, specify the **Network Name** on the Network Attributes screen, in the **Local network ID** parameter, and on the APPC controller description, in the **RMTNETID parameter**. For more information, see your APPN documentation.

## Remote node identifiers for connections

To specify the remote node where a connection should connect, you can use several types of parameters:

### Network name (remote node) and control point name (remote node)  

These two parameters work together. If either parameter is supplied, make sure to also supply the other parameter. These parameters are used only for Format 3 exchange identifications (XIDs), one of two types of exchange identification. Format 3 XIDs are generally used for APPC. If a connection doesn't use Format 3 XIDs, there is no need to specify these parameters.

As a general guideline, if the administrator of the remote host, peer, or downstream system uses these parameters, use the same parameters.
  
### Remote node ID  

You can use this parameter in a Format 0 XID or Format 3 XID, which are the two types of identification exchange. Format 0 XID is generally used for 3270 communication and for LUA, while Format 3 XID is generally used for APPC.  

As a general guideline, if the administrator of the remote host, peer, or downstream system uses this parameter, use the same parameter.

## Local and remote names  

The **Network Name** and **Control Point Name** for the remote node differ from the **Network Name** and **Control Point Name** for the local node. You specify the remote **Network Name** and **Control Point Name** in the **Connection Properties** box. You specify the local **Network Name** and **Control Point Name** in the **Server Properties** box.
  
## Primary configuration server

The primary configuration server is the HIS computer designated to contain the domain-wide configuration file. The configuration file reflects the HIS resources for the SNA subdomain, including all HIS computers, link services, LUs, 3270 users, and so on. Only one primary server can exist in the subdomain.  
  
## Backup configuration server

The backup configuration server is an HIS computer on which the configuration file is replicated by HIS. You can have more than one backup server in an SNA subdomain. If the primary HIS computer goes down, HIS loads the copy of the configuration file located on a backup HIS computer. In this case, you can start and stop servers and connections, but you can't change or save the configuration.

## Identifiers in incoming XIDs

When you're deciding the type of remote node identifier to specify for a connection that accepts incoming calls, you might find it helpful to learn and understand how HIS uses exchange identifications (XIDs) from incoming calls.

When HIS receives an XID from an incoming call, HIS looks at the XID for some type of identifier of the remote system that made the call. HIS compares this identifier, in the order described in the following list, against identifiers stored in the HIS configuration. If HIS finds a match, HIS accepts the call. If HIS finds that identifiers are left unspecified, in the configuration or the XID, and the connection is an SDLC connection, HIS accepts the call, pending further exchange of information.
  
HIS compares identifiers in the following order:

1. If the incoming XID is Format 3, HIS examines the XID for a remote node Network Name and Control Point Name.

   If these parameters exist in both the incoming XID and in the HIS configuration, and they match, HIS accepts the call. If the parameters exist but don't match, HIS rejects the call.

1. If the parameters are unavailable for the preceding step, HIS next examines remote node IDs.

   These IDs might be used in either Format 0 or Format 3 XIDs. If a remote node ID exists in both the incoming XID and in the HIS configuration, and they match, HIS accepts the call. If the parameters exist but don't match, HIS rejects the call.
   
## See also

[Understanding Connectivity](understanding-connectivity1.md)
