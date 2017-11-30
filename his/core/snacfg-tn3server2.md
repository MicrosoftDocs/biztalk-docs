---
title: "Snacfg TN3Server2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d646625-9f14-4fed-86b1-4879e361ec16
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Snacfg TN3Server
## Purpose  
 Allows you to view, add, delete, or modify TN 3270 servers. This command can also be used to add a TN 3270 server, though the SNA Manager is the recommended interface for adding servers.  
  
> [!NOTE]
>  Configuration settings specified with snacfg tn3server correspond to server settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] TN3Servername [configpath] TN3Servernname [configpath] TN3Servernname [options]  
[configpath] TN3Servername [options]  
[configpath] TN3Servername  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of the TN 3270 servers on the local subdomain.  
  
 *tn3servername*  
 Specifies the computer name of the TN 3270 server on which settings will be viewed or changed.  
  
 **/print**  
 Displays a list of the configuration settings of a print session. The displayed command does not contain the word **snacfg**, so that it can be redirected to a command file. Command files are discussed earlier in this section.  
  
 **/add**  
 Adds a TN 3270 Server computer called *tn3servername*. For adding a server, the recommended method is to use the SNA Manager, not **snacfg tn3server**.  
  
 Before you can add connections to the server, link services must also be configured for the server. The recommended interface for configuring link services is the SNA Manager.  
  
 **/delete**  
 Deletes *tn3servername*.  
  
## Options for TN 3270 Servers  
 **/logauditevents:{ yes &#124; no }**  
 Specifies whether the TN service uses the event log to log informational messages as well as error conditions. These are messages that log successful client connection and successful client termination.  
  
 **/snaeventlog:{ yes &#124; no }**  
 Specifies whether the TN service uses the same event log as the SNA Manager. If this is set to *yes*, all TN3270 service event messages are written to the event log being used by the Host Integration Server system. If this is set to *no*, all TN3270 service event messages are written to the Windows Event Log on the local machine.  
  
 **/nameresolution:{ yes &#124; no }**  
 Name resolution should only be selected if you are running a domain name resolver. A domain name resolver catalogs IP addresses and corresponding network names of connected computers. The domain name resolver allows you to enter the name of a computer rather than the IP address when an IP address is required.  
  
 **/closelistensocket:{ yes &#124; no }**  
 By default, the TN3270 Service always has a socket open for listening for incoming requests. If this option is turned on, the TN3270 Service stops listening on this socket once all of its defined LUs are in use. The purpose of this is to work with emulators that can try to connect to a number of computers running TN3270 Service and that connect to whichever computer accepts their connection attempt. In this case, it is useful if a computer with no LUs available is not listening.  
  
 **/tn3270modeonly:{ yes &#124; no }**  
 The TN3270 Service now supports TN3270E, an enhancement to TN3270. When a client first connects to a computer running TN3270 Service, it negotiates which functions they both support. TN3270 emulators should be able to negotiate with TN3270 Service, if only to state that they do not support TN3270E. However, some TN3270 emulators are unable to negotiate properly with TN3270 Service, causing the negotiation to fail. For this reason the TN3270 Service has an option to default to TN3270 mode and not to use TN3270E features, so that these TN3270 negotiation problems do not occur.  
  
 **/printerflowcontrol:{ yes &#124; no }**  
 If a TN3270 Server adheres strictly to the specification described in RFC 1647, there is no way of implementing flow control between a computer running TN3270 Service and a TN3270 client. In practice this causes no problems for display emulators, but it does cause a problem for printer emulators, which can be swamped with data and have no way of notifying the TN3270 Service that they cannot process any more messages. If this option is turned on, the TN3270 Service sends all messages to a TN3270 printer client as RESPONSE-REQUIRED, and does not send any messages until it has received a response for the previous message.  
  
 **/idletimeout:** *value  1-1440*  
 Specifies time limits in seconds. If the session is inactive for this length of time, then TN3270 Service disconnects the client.  
  
 **/initstatusdelay:** *value  (0-86400)*  
 Specifies time limits. This is the delay between the time when TN3270 Service connects to a host session and the time the TN3270 Service starts updating the client screen. There are often a large number of startup messages when the TN3270 Service first connects to a host session, and this option gives the user the opportunity not to receive them all.  
  
 **/msgclosedelay:** *value  (0-86400)*  
 Specifies time limits. When TN3270 Service forces a client to disconnect (for example, when the Host Integration Server session to the host has been lost), it sends the client an error message to be displayed on the screen. This value specifies the time between sending the message to the client and closing the socket with the client (which causes some clients to clear the screen, and so erase the message).  
  
 **/refreshcycletime:** *value  (0-60)*  
 Specifies time limits. This is the delay between updates of the status on the display.  
  
 **/inboundrusize:** *value  (256-32768)*  
 This controls the RU size (SNA message size) used by the TN3270 Service for logon messages to and from the host. The minimum value for inbound or outbound RU size is 256 bytes. If the host application sends large logon screens, these values should be increased.  
  
 **/outboundrusize:** *value  (256-32768)*  
 This controls the RU size (SNA message size) used by the TN3270 Service for logon messages to and from the host. The minimum value for inbound or outbound RU size is 256 bytes. If the host application sends large logon screens, these values should be increased.  
  
 **/portnumber:** *value*  
 Specifies the port number associated with telnet. You can type another port number to override the default value for a given session. TN services listen on multiple ports simultaneously. You can set a default port number for the TN service (assign the port number to the server) and override this number on a per session basis (assign the port number to the LU session), allowing a single client to connect to multiple host computers.  
  
 **/comment:**" *text*"  
 Adds an optional comment for the specified server. The comment can contain as many as 25 characters; enclose the comments in quotes.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)