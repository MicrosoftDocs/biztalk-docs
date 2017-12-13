---
title: "Snacfg Connection1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc0f900e-c7da-40f0-818f-89e285639f40
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Snacfg Connection
## Purpose  
 Allows you to view, add, delete, or modify connections, including peer connections (necessary for APPC LUs) or downstream connections.  
  
 Before configuring a connection, you must configure the server and link service that the connection will use.  
  
> [!NOTE]
>  Configuration settings specified with snacfg connection correspond to connection settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] connectionname [configpath] connectionname    servername{  [options]  
[configpath] connectionname [options]  
[configpath] connectionname /  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of configured connections.  
  
 *connectionname*  
 Specifies a name for the connection to be configured or viewed. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. A new connection name cannot be the same as any other connection name in the installation, and cannot be the reserved name SNASERVR.  
  
 If no options are specified after *connectionname*, the command-line interface displays a list of the configuration settings for the specified connection.  
  
 **/add**  
 Adds a connection called *connectionname*. To configure the connection, either specify other options after **/add**, or specify configuration options in additional **snacfg connection** commands (using the same *connectionname*).  
  
 **/delete**  
 Deletes *connectionname*.  
  
## Options Used with All Connection Types  
 **/server:** *servername*  
 Specifies the server to which to assign or move the connection. When **/add** is used, this option is required. The server name should be in the format machine_name or \\\machine_name\snaservr (for specifying the primary node on the machine) and \\\machine_name\snasrv02 (or snasrv03, snasrv04, and so on) for specifying the secondary nodes on the machine.  
  
 **/conntype:{ 802.2 &#124; SDLC &#124; X.25 &#124;  CHANNEL &#124; TWINAX }**  
 Specifies the connection type. When **/add** is used, this option is required.  
  
 **/comment:**" *text*"  
 Adds an optional comment for the specified connection. The comment can contain as many as 25 characters; enclose the comment in quotes.  
  
 **/linkservice:** *linkname*  
 Specifies the name of the link service to be used by *connectionname*. The link service type must match the connection type (802.2, SDLC, or X.25), or the **snacfg** command will not run.  
  
 In order for the link service to function correctly, it must be installed with the SNA Manager. Link services can also be installed with **snacfg link**; however, the SNA Manager is the recommended interface for installing link services, because it helps ensure that the resulting configuration is functional.  
  
 **/activation:{ onserverstartup &#124; ondemand &#124; byadministrator }**  
 For outgoing calls on *connectionname*, tells how the connection will be activated: on server startup, on demand, or by the administrator. (For incoming calls, activation is irrelevant, since the connection always begins listening for calls on server startup.)  
  
 If no value has been specified for **/activation**, the default for 802.2 (token ring or Ethernet) connections is **onserverstartup**. For all other connections, the default is **ondemand**.  
  
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
  
 **/remoteend:{ Host &#124; Ppeer &#124; downstream &#124; PUPassThrough}**  
 Specifies whether the connection is to be a host, peer, downstream, or passthrough.  
  
 **/remotenodeno:** *hexdigits*  
 Specifies the remote node number, a five-digit hexadecimal number. The remote node number forms the last part of the Remote Node ID, an eight-digit hexadecimal number that identifies the remote system.  
  
 **/xidtype:{ format0 &#124; format3 }**  
 Specifies the XID type, the type of identifying information for [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] to send. The choices are **format0** (Format 0) and **format3** (Format 3). Format 0 sends only the Node ID. Format 3 sends up to 100 bytes of identifying information, including the local node ID and control point name.  
  
 If no XID type has been specified, the default is **format3**.  
  
 **/calldirection:{ Incoming** &#124;  **Outgoing** &#124;  **Both }**  
 This option specifies the call direction.  
  
 **/channeladdress:** *hex string*  
 Specifies the channel sub address for channel attach connections. *Hex string* is a two-digit hexadecimal number, valid range 00..FF.  
  
 **/localsap:** *hexnum*  
 Specifies the local System Access Point (SAP). Enter a hexadecimal number between 04 and EC that is a multiple of 4. For example, *snacfg connection thisconn /localsap:7C*.  
  
 **/localcpname:** *text*  
 The Local Control Point Name works with the Network Name to identify a system. The maximum length is eight characters.  
  
 **/localnetname:** *text*  
 The Local Network Name works with the Local Control Point Name to identify a system. The maximum length is eight characters.  
  
 **/compression:{ None &#124; RLE &#124; LZ9 }**  
 These options offer progressively better compression, but at a progressively higher CPU usage cost.  
  
 **/passthruconn:** *text*  
 Specifies the name of the PU Passthrough connection.  
  
 **/peerdlcrole:{ Primary &#124; Secondary &#124; Negotiable }**  
 Specifies the role used in peer-to-peer communications.  
  
 **/dynamicludef:{ yes &#124; no }**  
 Specifies that this connection supports dynamic remote APPC LU allocation.  
  
## Additional Options Used with Downstream Connections  
 **/insert:**  *luname* **[,**   
 ***luname* ,]**  
 Assigns a downstream LU or pool to a downstream connection. Separate multiple LU or pool names with commas.  
  
 The downstream LU or pool named by ***luname*** must already exist. (A downstream LU can be created with **snacfg LUD**, and a downstream pool can be created with **snacfg poold**.) The connection named by *connectionname* must be a downstream connection. If these conditions are not met, the command is not processed.  
  
 **/remove:**  *luname* **[,**   
 ***luname* ,]**  
 Removes the assignment of a downstream LU or pool to a downstream connection. Separate multiple LU or pool names with commas.  
  
## Additional Options Used with 802.2 (Token Ring or Ethernet) Connections  
 **/remotenetaddr:** *hexdigits*  
 Specifies the 12-digit hexadecimal network address of the remote host to which this connection provides access.  
  
 If no remote network address has been specified, the default is 400000000000.  
  
 **/remotesapaddr:** *hexdigits*  
 Specifies the remote SAP address, which is a two-digit hexadecimal number, a multiple of 4, between 04 and EC. A value of 04 is recommended for most installations.  
  
 If no remote SAP address has been specified, the default is 04.  
  
 **/maxbtulen:** *value*  
 Specifies the maximum length for the BTU, which is the number of bytes that can be transmitted in a single data-link control frame.  
  
 The range is from 265 through 16393. If no maximum BTU length has been specified, the default is 1929.  
  
 **/receiveackthresh:** *value*  
 Specifies the receive ACK threshold, the maximum number of frames that the local system can receive from the remote system before sending a response.  
  
 The range is from 1 through 127. If no receive ACK threshold has been specified, the default is 2.  
  
 **/naksendlimit:** *value*  
 Specifies the unacknowledged send limit, the maximum number of frames that the local system can send without receiving a response from the remote system.  
  
 The range is from 1 through 127. If no unacknowledged send limit has been specified, the default is 1.  
  
 **/retrylimit:** *value*  
 Specifies the retry limit, the number of times that the local system should retransmit a frame if no response is received from the remote system.  
  
 The range is from 0 through 255. A value of 0 means the system uses its internal default retry limit. If no retry limit has been specified, the default is 10.  
  
 **/xidretries:** *value*  
 Specifies the XID retries, the number of times that the local system should retransmit an XID (an identifying message) if no response is received from the remote system.  
  
 The range is from 0 through 30. If no XID retries value has been specified, the default is 3.  
  
 **/t1timeout:{ Default**&#124; **200ms**&#124; **400ms**&#124; **600ms**&#124; **800ms**&#124; **1000ms &#124; 1s**&#124; **2s**&#124; **3s**&#124; **4s &#124; 5s}**  
 Specifies the amount of time that the local system should wait for the remote system to respond to a transmission before the local system tries again.  
  
 The values used for **Default** for **t1timeout** are 400 milliseconds for a local ring and 2 seconds for a remote ring.  
  
 **/t2timeout:{ Default**&#124; **40ms**&#124; **80ms**&#124; **120ms**&#124; **160ms**&#124; **200ms**&#124; **400ms**&#124; **800ms**&#124; **1200ms**&#124; **1600ms**&#124; **2000ms}**  
 Select the maximum amount of time that should be allowed before the local system sends an acknowledgment of a received transmission.  
  
 The values used for **Default** for **t2timeout** are 80 milliseconds for a local ring and 800 milliseconds for a remote ring.  
  
 **/titimeout:{ Default**&#124; **1s**&#124; **2s**&#124; **3s**&#124; **4s**&#124; **5s**&#124; **10s**&#124; **15s**&#124; **20s**&#124; **25s}**  
 Select the amount of time that the link can be inactive before the local system treats it as nonfunctioning and shuts it down.  
  
 The values used for **Default** for **titimeout** are 5 seconds for a local ring and 25 seconds for a remote ring.  
  
 **/activatedelay:{ Default** &#124;  **5s** &#124;  **10s** &#124;  **15s** &#124;  **20s** &#124;  **25s** &#124;  **30s** &#124;  **35s** &#124;  **40s** &#124;  **45s** &#124;  **50s** &#124;  **55s** &#124;  **60s** &#124;  **65s** &#124;  **70s** &#124;  **75s** &#124;  **80s** &#124;  **85s** &#124;  **90s** &#124;  **95s** &#124;  **100s** &#124;  **105s** &#124;  **110s** &#124;  **115s** &#124;  **120s** &#124;  **125s** &#124;  **130s** &#124;  **135s** &#124;  **140s** &#124;  **145s** &#124;  **150s** &#124;  **155s** &#124;  **160s** &#124;  **165s** &#124;  **170s** &#124;  **175s** &#124;  **180s** &#124;  **185s** &#124;  **190s** &#124;  **195s** &#124;  **200s** &#124;  **205s** &#124;  **210s** &#124;  **215s** &#124;  **220s** &#124;  **225s** &#124;  **230s** &#124;  **235s** &#124;  **240s** &#124;  **245s** &#124;  **250s** &#124;  **255s }**  
 This value specifies the delay between successive attempts to activate a Host Integration Server connection.  
  
 **/activateretrylimit:{ None** &#124;  **1** &#124;  **2** &#124;  **3** &#124;  **4** &#124;  **5** &#124;  **6** &#124;  **7** &#124;  **8** &#124;  **9** &#124;  **10** &#124;  **15** &#124;  **20** &#124;  **25** &#124;  **30** &#124;  **35** &#124;  **40** &#124;  **45** &#124;  **50** &#124;  **55** &#124;  **60** &#124;  **65** &#124;  **70** &#124;  **75** &#124;  **80** &#124;  **85** &#124;  **90** &#124;  **95** &#124;  **100** &#124;  **105** &#124;  **110** &#124;  **115** &#124;  **120** &#124;  **125** &#124;  **130** &#124;  **135** &#124;  **140** &#124;  **145** &#124;  **150** &#124;  **155** &#124;  **160** &#124;  **165** &#124;  **170** &#124;  **175** &#124;  **180** &#124;  **185** &#124;  **190** &#124;  **195** &#124;  **200** &#124;  **205** &#124;  **210** &#124;  **215** &#124;  **220** &#124;  **225** &#124;  **230** &#124;  **235** &#124;  **240** &#124;  **245** &#124;  **250** &#124;  **255 }**  
 This option specifies the number of times the server will try to activate a connection.  
  
## Additional Options Used with SDLC Connections  
 **/dialdata:** *value*  
 Specifies the phone number stored for this connection. For a modem that accepts a phone number from Host Integration Server that is, a modem attached to an SDLC adapter with a built-in serial (COM) port  the dial data specifies the telephone number for Host Integration Server to send to the modem. In this case, the number should be in the format expected by the modem. For manually dialed modems, the dial data is displayed in a pop-up message when the connection is started, and can be in any format.  
  
 **/encoding:{ NRZI &#124; NRZ }**  
 Specifies the encoding scheme to be used by the modem. The choices are **nrzi**, nonreturn to zero inverted, and **NRZ**, nonreturn to zero.  
  
 The modem must use the same encoding scheme as the modem at the remote computer. For connections to host systems, the encoding scheme must match the value in the LINE/GROUP definition in VTAM.  
  
 If no encoding scheme has been specified, the default is NRZI.  
  
 **/duplex:{ half &#124; full }**  
 Specifies the modem duplex setting. The choices are **half**, for a half-duplex modem, and **full**, for a full-duplex modem. If you want to use the full-duplex setting, one or more of your adapters must have the constant carrier option set. The constant carrier option is set in the SNA Manager. The constant carrier option can also be set with **snacfg link**; however, the SNA Manager is the recommended interface for setting the constant carrier option and other link service options.  
  
 Most Host Integration Server computers will use the default for duplex, **half**.  
  
 **/datarate:{ high &#124; low }**  
 Specifies the data rate for transmissions between the Host Integration Server communications adapter and the modem. This rate can only be set for certain kinds of modems and adapters; for specific information, see the adapter and modem documentation.  
  
 A data rate of **high** gives faster transmissions; **low** gives more reliable transmissions and prevents the transmission errors sometimes caused by poor-quality lines at the high rate.  
  
 If no data rate has been specified, the default is **high**.  
  
 **/polladdress:** *hexdigits*  
 Specifies the poll address, a two-digit hexadecimal number. For connections to a host, the local poll address should match the VTAM PU definition for the ADDR= parameter.  
  
 Do not use 00 or FF for the poll address; these values are reserved. If no poll address has been specified, the default is C1.  
  
 **/idletimeout:** *value*  
 Specifies, in tenths of a second, the idle time-out. The idle time-out is the length of time that the local system should wait for the host to respond to a transmission, before the local system tries again. Too small a time-out can cause connection problems.  
  
 The range is from 1 (one-tenth of a second) through 300 (30 seconds). If no idle time-out has been specified, the default is 300 (30 seconds).  
  
 **/idleretrylimit:** *value*  
 Specifies the idle retry limit, the number of times the local system should try to poll or send data to the host if there is no response.  
  
 The range is from 1 through 255. If no idle retry limit has been specified, the default is 10.  
  
 **/contacttimeout:** *value*  
 Specifies the contact time-out: the length of time, in tenths of a second, which the local system should wait between attempts to make a connection with a remote system.  
  
 The range is from 5 (five-tenths of a second) through 300 (30 seconds). If no contact time-out has been specified, the default is 300 (30 seconds).  
  
 **/contactretrylimit:** *value*  
 Specifies contact retry limit, the maximum number of times the local system should attempt to make a given connection.  
  
 The range is from 1 through 20. If no contact retry limit has been specified, the default is 10.  
  
 **/switchedconntimeout:** *value*  
 Specifies the switched connection establishment time-out; used for switched SDLC lines (standard telephone lines) only. The switched connection establishment time-out is the number of seconds that will be allowed for the user or modem to dial the remote computer's number.  
  
 This parameter is ignored by incoming calls.  
  
 The range is from 10 through 500 seconds. If no switched connection establishment time-out has been specified, the default is 300.  
  
 **/multidropprimconn:{ yes &#124; no }**  
 Specifies whether this connection will be a multidrop primary connection.  
  
 A multidrop connection is one in which a primary node communicates with multiple secondary nodes concurrently over the same physical transmission medium.  
  
 **/selectstandby:{ yes &#124; no }**  
 Specifies whether the modem's standby line is set to "on." Standby can only be set for certain kinds of modems; for specific information, see the modem documentation.  
  
 If no setting has been specified for standby, the default setting is **no**.  
  
 **/sdlcmaxbtu:** *value*  
 Specifies the maximum length for the BTU, which is the number of bytes that can be transmitted in a single data-link information frame.  
  
 The range is from 265 through 16393. If no maximum BTU length for SDLC has been specified, the default is 265.  
  
 **/activatedelay:{ Default** &#124;  **5s** &#124;  **10s** &#124;  **15s** &#124;  **20s** &#124;  **25s** &#124;  **30s** &#124;  **35s** &#124;  **40s** &#124;  **45s** &#124;  **50s** &#124;  **55s** &#124;  **60s** &#124;  **65s** &#124;  **70s** &#124;  **75s** &#124;  **80s** &#124;  **85s** &#124;  **90s** &#124;  **95s** &#124;  **100s** &#124;  **105s** &#124;  **110s** &#124;  **115s** &#124;  **120s** &#124;  **125s** &#124;  **130s** &#124;  **135s** &#124;  **140s** &#124;  **145s** &#124;  **150s** &#124;  **155s** &#124;  **160s** &#124;  **165s** &#124;  **170s** &#124;  **175s** &#124;  **180s** &#124;  **185s** &#124;  **190s** &#124;  **195s** &#124;  **200s** &#124;  **205s** &#124;  **210s** &#124;  **215s** &#124;  **220s** &#124;  **225s** &#124;  **230s** &#124;  **235s** &#124;  **240s** &#124;  **245s** &#124;  **250s** &#124;  **255s }**  
 This value specifies the delay between successive attempts to activate a Host Integration Server connection.  
  
 **/activateretrylimit:{ None** &#124;  **1** &#124;  **2** &#124;  **3** &#124;  **4** &#124;  **5** &#124;  **6** &#124;  **7** &#124;  **8** &#124;  **9** &#124;  **10** &#124;  **15** &#124;  **20** &#124;  **25** &#124;  **30** &#124;  **35** &#124;  **40** &#124;  **45** &#124;  **50** &#124;  **55** &#124;  **60** &#124;  **65** &#124;  **70** &#124;  **75** &#124;  **80** &#124;  **85** &#124;  **90** &#124;  **95** &#124;  **100** &#124;  **105** &#124;  **110** &#124;  **115** &#124;  **120** &#124;  **125** &#124;  **130** &#124;  **135** &#124;  **140** &#124;  **145** &#124;  **150** &#124;  **155** &#124;  **160** &#124;  **165** &#124;  **170** &#124;  **175** &#124;  **180** &#124;  **185** &#124;  **190** &#124;  **195** &#124;  **200** &#124;  **205** &#124;  **210** &#124;  **215** &#124;  **220** &#124;  **225** &#124;  **230** &#124;  **235** &#124;  **240** &#124;  **245** &#124;  **250** &#124;  **255 }**  
 This option specifies the number of times the server will try to activate a connection.  
  
## Additional Options Used with SDLC Peer Connections  
 **/multidropprimconn:{ yes &#124; no }**  
 Specifies whether this server is to be the primary station for a multidrop connection on a leased SDLC line.  
  
 **/pollrate:** *value*  
 Specifies the poll rate in polls per second.  
  
 The range is from 1 through 50. If no poll rate has been specified, the default is 5.  
  
 **/activatedelay:{ Default** &#124;  **5s** &#124;  **10s** &#124;  **15s** &#124;  **20s** &#124;  **25s** &#124;  **30s** &#124;  **35s** &#124;  **40s** &#124;  **45s** &#124;  **50s** &#124;  **55s** &#124;  **60s** &#124;  **65s** &#124;  **70s** &#124;  **75s** &#124;  **80s** &#124;  **85s** &#124;  **90s** &#124;  **95s** &#124;  **100s** &#124;  **105s** &#124;  **110s** &#124;  **115s** &#124;  **120s** &#124;  **125s** &#124;  **130s** &#124;  **135s** &#124;  **140s** &#124;  **145s** &#124;  **150s** &#124;  **155s** &#124;  **160s** &#124;  **165s** &#124;  **170s** &#124;  **175s** &#124;  **180s** &#124;  **185s** &#124;  **190s** &#124;  **195s** &#124;  **200s** &#124;  **205s** &#124;  **210s** &#124;  **215s** &#124;  **220s** &#124;  **225s** &#124;  **230s** &#124;  **235s** &#124;  **240s** &#124;  **245s** &#124;  **250s** &#124;  **255s }**  
 This value specifies the delay between successive attempts to activate a Host Integration Server  
  
 **/activateretrylimit:{ None** &#124;  **1** &#124;  **2** &#124;  **3** &#124;  **4** &#124;  **5** &#124;  **6** &#124;  **7** &#124;  **8** &#124;  **9** &#124;  **10** &#124;  **15** &#124;  **20** &#124;  **25** &#124;  **30** &#124;  **35** &#124;  **40** &#124;  **45** &#124;  **50** &#124;  **55** &#124;  **60** &#124;  **65** &#124;  **70** &#124;  **75** &#124;  **80** &#124;  **85** &#124;  **90** &#124;  **95** &#124;  **100** &#124;  **105** &#124;  **110** &#124;  **115** &#124;  **120** &#124;  **125** &#124;  **130** &#124;  **135** &#124;  **140** &#124;  **145** &#124;  **150** &#124;  **155** &#124;  **160** &#124;  **165** &#124;  **170** &#124;  **175** &#124;  **180** &#124;  **185** &#124;  **190** &#124;  **195** &#124;  **200** &#124;  **205** &#124;  **210** &#124;  **215** &#124;  **220** &#124;  **225** &#124;  **230** &#124;  **235** &#124;  **240** &#124;  **245** &#124;  **250** &#124;  **255 }**  
 This option specifies the number of times the server will try to activate a connection.  
  
## Additional Options Used with X.25 Connections  
 **/remotex25addr:** *hexdigits*  
 Specifies the remote X.25 address, which identifies the remote system on an X.25 network. The address usually consists of 12 hexadecimal digits, but can contain up to 15 hexadecimal digits.  
  
 **/x25maxbtu:** *value*  
 Specifies the maximum length for the BTU, which is the number of bytes that can be transmitted in a single data-link information frame.  
  
 The range is from 265 through 16393. If no maximum BTU length for X.25 has been specified, the default (for host connections) is 265.  
  
 **/virtualcircuit:{ perm &#124; switched }**  
 Specifies the type of virtual circuit used by the connection. The choices are **perm** and **switched**. A **perm** circuit is constantly active and uses a preset destination address. A **switched** circuit is called and cleared dynamically, and uses a destination address that is supplied when the circuit is called.  
  
 If no virtual circuit type has been specified, the default is **switched**.  
  
 **/pvcalias:** *value*(for PVC only)  
 Specifies the PVC alias, the number that identifies the PVC channel: 1 for the first channel, 2 for the second, and so on. Used for PVCs only.  
  
 The range is from 1 through the number of configured PVC channels. If no PVC alias has been specified, the default is 1.  
  
 **/packetsize:** *value*(for PVC only)  
 Specifies packet size, the maximum number of data bytes (not header bytes) to be sent in a frame on this X.25 network. Used for PVCs only.  
  
 The possible values are 64, 128, 256, 512, and 1024. If no packet size has been specified, the default is 128.  
  
 **/windowsize:** *value*(for PVC only)  
 Specifies window size, the maximum number of frames that the local system can send without receiving a response from the remote system, on this X.25 network. Used for PVCs only.  
  
 The range is from 1 through 7. If no window size has been specified, the default is 2.  
  
 **/facilitydata:** *text*(for SVC only)  
 Specifies the codes for any facility data required by the network provider or by the administrator of the remote system. Used for SVCs only. Facility data can include as many as 126 hexadecimal characters (63 hexadecimal bytes).  
  
 Facility data is a coded string of information often used to request nondefault functions from the X.25 network for a particular SVC connection.  
  
 **/userdata:** *text*(for SVC only)  
 Specifies the codes for any user data required by the network provider. Used for SVCs only. The user data must be an even number of hexadecimal characters, up to the maximum of 32 characters.  
  
 User data is a coded string of information, specifying items such as the communications protocol used by the X.25 network (for SNA, this protocol must be QLLC, specified by C3).  
  
 The default for user data is C3; this specifies the QLLC protocol.  
  
 **/activatedelay:{ Default** &#124;  **5s** &#124;  **10s** &#124;  **15s** &#124;  **20s** &#124;  **25s** &#124;  **30s** &#124;  **35s** &#124;  **40s** &#124;  **45s** &#124;  **50s** &#124;  **55s** &#124;  **60s** &#124;  **65s** &#124;  **70s** &#124;  **75s** &#124;  **80s** &#124;  **85s** &#124;  **90s** &#124;  **95s** &#124;  **100s** &#124;  **105s** &#124;  **110s** &#124;  **115s** &#124;  **120s** &#124;  **125s** &#124;  **130s** &#124;  **135s** &#124;  **140s** &#124;  **145s** &#124;  **150s** &#124;  **155s** &#124;  **160s** &#124;  **165s** &#124;  **170s** &#124;  **175s** &#124;  **180s** &#124;  **185s** &#124;  **190s** &#124;  **195s** &#124;  **200s** &#124;  **205s** &#124;  **210s** &#124;  **215s** &#124;  **220s** &#124;  **225s** &#124;  **230s** &#124;  **235s** &#124;  **240s** &#124;  **245s** &#124;  **250s** &#124;  **255s }**  
 This value specifies the delay between successive attempts to activate a Host Integration Server connection.  
  
 **/activateretrylimit:{ None** &#124;  **1** &#124;  **2** &#124;  **3** &#124;  **4** &#124;  **5** &#124;  **6** &#124;  **7** &#124;  **8** &#124;  **9** &#124;  **10** &#124;  **15** &#124;  **20** &#124;  **25** &#124;  **30** &#124;  **35** &#124;  **40** &#124;  **45** &#124;  **50** &#124;  **55** &#124;  **60** &#124;  **65** &#124;  **70** &#124;  **75** &#124;  **80** &#124;  **85** &#124;  **90** &#124;  **95** &#124;  **100** &#124;  **105** &#124;  **110** &#124;  **115** &#124;  **120** &#124;  **125** &#124;  **130** &#124;  **135** &#124;  **140** &#124;  **145** &#124;  **150** &#124;  **155** &#124;  **160** &#124;  **165** &#124;  **170** &#124;  **175** &#124;  **180** &#124;  **185** &#124;  **190** &#124;  **195** &#124;  **200** &#124;  **205** &#124;  **210** &#124;  **215** &#124;  **220** &#124;  **225** &#124;  **230** &#124;  **235** &#124;  **240** &#124;  **245** &#124;  **250** &#124;  **255 }**  
 This option specifies the number of times the server will try to activate a connection.  
  
## Additional Options Used with Channel Connections  
 **/activatedelay:{ Default** &#124;  **5s** &#124;  **10s** &#124;  **15s** &#124;  **20s** &#124;  **25s** &#124;  **30s** &#124;  **35s** &#124;  **40s** &#124;  **45s** &#124;  **50s** &#124;  **55s** &#124;  **60s** &#124;  **65s** &#124;  **70s** &#124;  **75s** &#124;  **80s** &#124;  **85s** &#124;  **90s** &#124;  **95s** &#124;  **100s** &#124;  **105s** &#124;  **110s** &#124;  **115s** &#124;  **120s** &#124;  **125s** &#124;  **130s** &#124;  **135s** &#124;  **140s** &#124;  **145s** &#124;  **150s** &#124;  **155s** &#124;  **160s** &#124;  **165s** &#124;  **170s** &#124;  **175s** &#124;  **180s** &#124;  **185s** &#124;  **190s** &#124;  **195s** &#124;  **200s** &#124;  **205s** &#124;  **210s** &#124;  **215s** &#124;  **220s** &#124;  **225s** &#124;  **230s** &#124;  **235s** &#124;  **240s** &#124;  **245s** &#124;  **250s** &#124;  **255s }**  
 This value specifies the delay between successive attempts to activate a Host Integration Server connection.  
  
 **/activateretrylimit:{ None** &#124;  **1** &#124;  **2** &#124;  **3** &#124;  **4** &#124;  **5** &#124;  **6** &#124;  **7** &#124;  **8** &#124;  **9** &#124;  **10** &#124;  **15** &#124;  **20** &#124;  **25** &#124;  **30** &#124;  **35** &#124;  **40** &#124;  **45** &#124;  **50** &#124;  **55** &#124;  **60** &#124;  **65** &#124;  **70** &#124;  **75** &#124;  **80** &#124;  **85** &#124;  **90** &#124;  **95** &#124;  **100** &#124;  **105** &#124;  **110** &#124;  **115** &#124;  **120** &#124;  **125** &#124;  **130** &#124;  **135** &#124;  **140** &#124;  **145** &#124;  **150** &#124;  **155** &#124;  **160** &#124;  **165** &#124;  **170** &#124;  **175** &#124;  **180** &#124;  **185** &#124;  **190** &#124;  **195** &#124;  **200** &#124;  **205** &#124;  **210** &#124;  **215** &#124;  **220** &#124;  **225** &#124;  **230** &#124;  **235** &#124;  **240** &#124;  **245** &#124;  **250** &#124;  **255 }**  
 This option specifies the number of times the server will try to activate a connection.  
  
 **/controlunit:** *value (0x0-0xf)*  
 Sets the value of the control unit image number.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)