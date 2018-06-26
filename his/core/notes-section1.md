---
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
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Notes Section
This section contains notes about AS/400 computers, local and remote names, time-outs for 802.2 connections, and adapter and adapter addresses.  
  
## Note About AS/400 Computers  
 To connect to an AS/400 computer, supply both local node and remote node parameters for the Network Name and the Control Point Name. These properties are configured in separate dialog boxes:  
  
- **Local node (server) properties.** In the **Server Properties** dialog box of the computer running Host Integration Server, type the **Control Point Name** and the **Network Name**. The server Network Name must correspond to the RMTNETID parameter in the AS/400 APPC controller description. (The default for the AS/400 computer network ID is typically APPN.) If this value is set to **\*SAME**, refer to the Local Network ID parameter in the AS/400 Network Attributes screen (using the **dspneta** command). The server Control Point Name must match the RMTCPNAME parameter in the AS/400 APPC controller description. For 802.2 connections, the AS/400 computer can be configured to automatically create the APPC controller description when the computer running [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] first connects to the AS/400 computer, by setting the AUTOCRTCTL parameter to **\*YES** in the AS/400 Token-Ring or Ethernet line description. However, for SDLC connections, the APPC controller description must be manually created.  
  
   If you specify a CPNAME in **Connection Properties**, it overrides the CPNAME in the **Server Properties** dialog box. The CPNAME in **Server Properties** is the default and will be used unless it is changed in **Connections Properties**.  
  
- **Remote node (connection) properties.** In the **Properties** dialog box for an 802.2 or SDLC connection, type the **Network Name** and **Control Point Name (CP name)** of the AS/400 computer into the **Network Name (Remote Node)** and **Control Point Name (Remote Node)** fields. The AS/400 Network Name and Local Control Point Name can be found on the AS/400 Network Attributes screen using the DSPNETA. For more information about these fields, click Help on the **Properties** dialog box for the connection.  
  
   On an AS/400 computer, the Network Name is specified in the Local network ID parameter in the Network Attributes screen and in the RMTNETID parameter on the APPC controller description. For more information, see your APPN documentation.  
  
## Using Remote Node Identifiers  
 You can use several types of parameters to specify the remote node with which a connection should connect:  
  
## Remote address (802.2 connections only)  
 This parameter is required for 802.2 connections. For outgoing calls, it is used to specify the remote host, peer, or downstream system being called. This parameter is the **Remote Network Address**.  
  
## Network Name (Remote Node) and Control Point Name (Remote Node)  
 As a general guideline, use these parameters if the administrator of the remote host, peer, or downstream system uses them.  
  
 These two parameters work together; if either parameter is supplied, the other should also be supplied. These parameters are used only for Format 3 exchange identifications (XIDs), one of two types of exchange identification. Format 3 XIDs are generally used for APPC. If a connection does not use Format 3 XIDs, there is no need to specify these parameters.  
  
## Remote Node ID  
 As a general guideline, use this parameter if the administrator of the remote host, peer, or downstream system uses it. This parameter can be used in Format 0 XIDs or Format 3 XIDs, the two types of identification exchange. **Format 0 XID**s are generally used for 3270 communication and for LUA; **Format 3 XID**s are generally used for APPC.  
  
## Note About Local and Remote Names  
 The **Network Name** and **Control Point Name** for the remote node are different from the **Network Name** and **Control Point Name** for the local node. The remote **Network Name** and **Control Point Name** are specified in the **Connection Properties** dialog box. The local **Network Name** and **Control Point Name** are specified in the **Server Properties** dialog box.  
  
## Configuring Multidrop Connections  
 In a multidrop connection, one primary computer communicates simultaneously with multiple secondary computers. Host Integration Server supports multidrop connections used for downstream systems on leased SDLC lines.  
  
 You can configure up to four multidrop connections on each line, with a computer running Host Integration Server as the primary server on each.  
  
 Configure each connection to be used in the multidrop configuration according to the instructions that follow.  
  
#### To configure multidrop connections  
  
1. Configure a link service for an SDLC line with the **Constant RTS** option not selected.  
  
2. Configure each connection to be used in the multidrop configuration as follows:  
  
   -   In the **SDLC Properties** dialog box, select the same link service for each connection.  
  
   -   In the **SDLC Properties** dialog box, under **Remote End**, select **Downstream**.  
  
   -   Make all the parameters identical for each configuration, except for **Poll Address**, and possibly the **Local Node ID** and **Remote Node ID**. For these parameters, obtain values from the downstream system administrators. Make the **Poll Address** unique for each station.  
  
3. For the primary connection in the multidrop configuration, on the SDLC page of the **SDLC Properties** dialog box, select the **Multidrop Primary** box.  
  
   For information about using the configuration dialog boxes, click **Help** in the **SDLC Properties** dialog box.  
  
## Note About Time-outs for 802.2  
 The time-outs for 802.2 (**t1**, **t2**, and **ti**) are derived from basic timer values that are set in the Windows registry. Host Integration Server is designed with the assumption that these registry values will not be changed after they have been set by the DLC (802.2) driver. If these registry values are changed, the choices displayed in the **Response Timeout**, **Receive ACK Timeout**, or **Inactivity Timeout** fields may no longer reflect the actual amounts of time that Host Integration Server waits.  
  
## Simplified Facility Data Example  
 The following simplified example shows how identifiers allow each facility request to be distinguished from the ones that follow:  
  
 40AAAA20BB  
  
 The example contains two requests. The first request begins with a 4, indicating that after the two-character identifier there are four characters (in this case, four occurrences of the A character). The second request follows, beginning with a 2, indicating that after the two-character identifier there are two characters (two occurrences of the B character).  
  
## Standard Facility Data Example  
 The facility data string in this example initiates a connection using 256-byte packets, a sending window of 7, a receive window of 4, and charges reversed. The facility requests that do this are as follows:  
  
- 42 08 08 for Packet Size  
  
- 43 04 07 for Window Size  
  
- 01 01 for reverse charging  
  
  When these requests are concatenated, the following facility data string is created:  
  
  4208084304070101  
  
## Common Identifier Table  
 The following table shows commonly used identifiers for facility requests.  
  
|Facility|Identifier|Parameters|Meaning|  
|--------------|----------------|----------------|-------------|  
|Reverse charging|01|00 01|Reverse charging NOT requested Reverse charging requested|  
|Packet Size|42|0r0s|r = Receive Packet Size s = Send Packet Size|  
||||r and s can have the following values:|  
||||6 for 64-byte packets 7 for 128-byte packets 8 for 256-byte packets 9 for 512-byte packets A for 1024-byte packets|  
|Window Size|43|0r0s|r = Receive Window Size s = Send Window Size r and s can be from 1 through 7.  They are usually set equal,  making the send and receive  windows the same size.|  
  
 In this table, send and receive operate from the view of the initiator of the connection.  
  
## Note About Local Adapter Address  
 When communicating with the administrator of a remote host, peer, or downstream system, you may need to tell that administrator the address of your local adapter.  
  
 To determine the local address of an 802.2 adapter, at the command prompt, type:  
  
 **net config server**  
  
 In the resulting display, the address of the local adapter appears in the line labeled **Server is Active On**.  
  
## Primary Configuration Server  
 The primary configuration server is the Host Integration Server computer designated to contain the domain-wide configuration file. The configuration file reflects the Host Integration Server resources for the SNA subdomain, including all Host Integration Server computers, link services, LUs, 3270 users, and so on. There can be only one primary server in the subdomain.  
  
## Backup Configuration Server  
 The backup configuration server is a Host Integration Server computer on which the configuration file is replicated by Host Integration Server. There can be more than one backup server in an SNA subdomain. Host Integration Server will load the copy of the configuration file located on a backup Host Integration Server computer if the primary Host Integration Server computer goes down. In this case, servers and connections can be started and stopped, but the configuration cannot be changed or saved.  
  
## Identifiers in Incoming XIDs  
 When deciding which type of remote node identifier to specify for a connection that accepts incoming calls, it may be helpful to understand how Host Integration Server uses exchange identifications (XIDs) from incoming calls.  
  
 When Host Integration Server receives an XID from an incoming call, it looks at the XID for some type of identifier of the remote system that made the call. It compares this identifier, in the order shown in the following list, against identifiers stored in the Host Integration Server configuration. If it finds a match, it accepts the call. If it finds that identifiers are left unspecified (in the configuration or the XID), and the connection is an SDLC connection, Host Integration Server accepts the call, pending further exchange of information. In other cases—when every comparison yields a mismatch, or when identifiers are left unspecified but the connection is 802.2—Host Integration Server rejects the incoming call.  
  
 Identifiers are compared in the following order:  
  
1.  If the incoming XID is Format 3, Host Integration Server examines the XID for a remote node Network Name and Control Point Name. If these parameters are present in both the Incoming XID and in the Host Integration Server configuration, and they match, the call is accepted. If the parameters are present and do not match, the call is rejected.  
  
2.  If the parameters were not available for the preceding step, Remote Node IDs are examined next. (Remote Node IDs may be used in either Format 0 or Format 3 XIDs.) If a Remote Node ID is present in both the Incoming XID and in the Host Integration Server configuration, and they match, the call is accepted. If the parameters are present and do not match, the call is rejected.  
  
3.  If the parameters were not available for the preceding steps, for 802.2 connections, remote addresses are examined:  
  
     For 802.2 connections, the Remote Network Address in the Host Integration Server configuration is compared to the address from which the XID was received. If the addresses match, the call is accepted; if not, the call is rejected.  
  
4.  For 802.2 connections, if no match is found in any of the preceding steps, the incoming call is rejected.  
  
     For SDLC connections, if no match is found in the preceding steps, but identifiers were left unspecified in the configuration or the XID, the call is accepted, pending further exchange of identifiers. However, if identifiers were not left unspecified and no identifiers match, the call is rejected.  
  
## Guidelines for Identifiers for 802.2 Connections  
 The following table lists guidelines for identifiers for 802.2 connections.  
  
|Conn. type|Allowed call directions|Guidelines for identifiers for remote node|  
|----------------|-----------------------------|------------------------------------------------|  
|802.2|Outgoing|Use Remote Network Address|  
|802.2|Incoming|Match the identifiers used on the remote system:     Remote node Network Name and Control Point Name     or     Remote Node ID     or     Remote Network Address|  
|802.2|Both|Use a combination of outgoing plus incoming identifiers|  
  
## Guidelines for Identifiers for SDLC Connections  
 The following table lists guidelines for identifiers for SDLC connections.  
  
|Conn. type|Allowed call directions|Guidelines for identifiers for remote node|  
|----------------|-----------------------------|------------------------------------------------|  
|SDLC|Outgoing|If Host Integration Server supplies the phone number to the modem, specify Dial Data (phone number of remote system)|  
|SDLC|Incoming|Match the identifiers used on the remote system:     Remote node Network Name and Control Point Name     or     Remote Node ID|  
|SDLC|Both|Use a combination of outgoing plus incoming identifiers|  
  
## See Also  
 [Understanding Connectivity](../core/understanding-connectivity1.md)