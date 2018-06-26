---
title: "TN3270 Properties: General2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_TN3270Service"
ms.assetid: 2d4ba716-2681-451a-b859-4e95d3fa2640
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TN3270 Properties: General
**Name**  
 Displays the name of the server running the TN3270 service. This field cannot be edited here.  
  
 **Comment**  
 Optionally, type a comment of up to 25 characters.  
  
 **Use Name Resolution**  
 Name Resolution should only be selected if you are running a domain name resolver. A domain name resolver catalogs IP addresses and corresponding network names of connected computers. The domain name resolver allows you to enter the name of a computer rather than the IP address when an IP address is required.  
  
 **TN3270 Mode only**  
 The TN3270 service also supports TN3270E, an enhancement to TN3270. When a client computer first connects to a computer running TN3270 service it negotiates which functions they both support. TN3270 emulators should be able to negotiate with TN3270 service, if only to state that they do not support TN3270. However, some TN3270 emulators are unable to negotiate properly with TN3270 service, causing the negotiation to fail. For this reason the TN3270 service has an option to default to TN3270 mode and not to use TN3270 features, so that these TN3270 negotiation problems do not occur.  
  
 **Printer Flow Control**  
 If a TN3270 service adheres strictly to the specification described in RFC 1647, there is no way of implementing flow control between a computer running TN3270 service and a TN3270 client. In practice this causes no problems for display emulators, but it does cause a problem for printer emulators, which can be overloaded with data and have no way of notifying the TN3270 service that they cannot process any more messages. If this option is turned on, the TN3270 service sends all messages to a TN3270 printer client as RESPONSE-REQUIRED, and does not send any messages until it has received a response for the previous message.  
  
 **Close Listen Socket**  
 By default the TN3270 service always has a socket open to listen for incoming requests. If this option is turned on, the TN3270 service stops listening on this socket after all of its defined LUs are in use. The purpose of this is to work with emulators that can try to connect to a number of computers running TN3270 service and that connect to whichever computer accepts their connection attempt. In this case it is useful if a computer with no LUs available is not listening.  
  
 **Log Normal Audit Events**  
 If this is set, audit messages are logged. These are messages that log successful client connection and successful client termination.  
  
 **Use SNA Event Log**  
 If this is selected, all TN3270 service event messages are written to the event log being used by the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] system. If this is not set, all TN3270 service event messages are written to the Windows event log on the local machine.  
  
## TN3270 Properties: Port/Security  
 This property page contains two groups.  
  
 The **Defined ports** group displays information pertaining to the currently configured 3270 Server ports.  
  
 The **Configure ports** group consists of controls for adding, editing, and deleting port configurations.  
  
## Defined ports  
 **Port**  
 Lists all ports and corresponding Security settings. On a new installation, setup automatically defines Port 23 as the Default Port.  
  
 **Security**  
 Displays the level of encryption/authentication assigned to that port. Values are High (168), Medium (128), Low (40), and Unsecured (TLS/SSL not enabled). Default is **Unsecured**.  
  
 **Client certificate**  
 Displays status: Required or Not required. Default is **Not Required**.  
  
 **Comment**  
 Displays a comment.  
  
## Port configuration  
 **Port**  
 Enter a valid port number from 1-65535.  
  
 **Security**  
 Choose a setting from the list: High (168), Medium (128), Low (40), or Unsecured. Default is **Unsecured**.  
  
 **Comment**  
 This is optional. Maximum length allowed is 25 characters.  
  
 **Verify client certificate**  
 If selected, the client will have to provide a valid certificate to make the connection. Default is not selected. If Security level is set to Unsecured, this option is unavailable.  
  
 The client requires a valid Certificate with the following properties:  
  
- Type X509  
  
- Client Authentication  
  
- Associated private key  
  
  These certificate settings may match some of those you would not choose to grant access to. It is therefore recommended that you check the list of default Trusted Root Certification Authorities in the TN3270 Service Store, and remove any you do not want to be there.  
  
  TN services listen on multiple ports simultaneously. You can set a default port number for the TN service (assign the port number to the server) and override this number on a per session basis (assign the port number to the LU session), allowing a single client computer to connect to multiple host computers.  
  
  You can also add the TN3270 port by using the SnaCfg tool, with the command and parameters shown below:  
  
```  
TN3PORT tn3270Server:PortNumber /ADD  
   /COMMENT:"comment"  
   /SECURITY:{ None | Low | Medium | High }  
   /CLIENTSertVALAUTH:{ Yes | No }  
  
```  
  
 The properties of the command are described in the following table:  
  
|Property or Method|Description|Validation|  
|------------------------|-----------------|----------------|  
|/COMMENT:Text|The comment field|0 – 25 characters|  
|/SECURITY:Type|Security level|None, Low, Medium or High|  
|/CLIENTCertVAL:YesNo|Indicates whether the client certificate verification is enabled|No – disabled<br /><br /> Yes - enabled|  
  
 **Default Port**  
 On a new installation, setup automatically defines Port 23 as Default Port. There can only be one default port at a time. After a port has been designated Default Port, it cannot be deleted until another Default Port has been selected. The default is **Not Selected**.  
  
## Adding Ports and Security  
 This property page allows increased security through support for Secure Sockets Layer (SSL) and TLS for all network transport-level services.  
  
 Although the Microsoft 3270 Client (emulator) does not support SSL or TLS, many third-party software vendors offer 3270 emulators that support this functionality, including Attachmate, IBM, NetManage, and WRQ.  
  
#### To add a new port  
  
1.  On the **TN3270 Properties: Port/Security** page, click **New**.  
  
2.  Enter the port number and select a security level (default is Unsecured). You can also add a comment and make this the default TN3270 Server port.  
  
3.  For maximum security, check the Client Certificate checkbox.  
  
#### To edit the properties of an existing port  
  
1.  On the **TN3270 Properties: Port/Security** page, highlight the port.  
  
2.  Click Edit.  
  
3.  When you are finished, click **Save**.  
  
## TN3270 Properties: Settings  
 **Idle Timeout**  
 Specify time limits. Allows the administrator to configure the TN3270 service to automatically terminate sessions that have been idle for a given time period.  When enabled, the TN3270 service will monitor the session's activity.  If the session becomes inactive for a period longer than the Idle Timeout, the TN3270 service will disconnect the client system and terminate the host session.  This setting is useful when there are a limited number of LUs available, as it will free up sessions that are no longer in use.     
  
 **KeepAlive Interval** 
 Specify time limits.  Allows the administrator to configure the TN3270 service to detect and terminate sessions that are no longer connected. When enabled, the TN3270 service will send a timing mark message at the interval specified.  If the client does not respond to this message, the TN3270 service will terminate the host session.  This setting is useful when there are long running sessions with intermittent traffic such as printer session.  Whereas the Idle Timeout would prematurely disconnect these sessions, the KeepAlive will actively detect whether the sessions are still present.  This setting is also useful for cleaning up sessions that have been disconnected by an interruption such as a network outage, which would normally leave the LU in session and not allow the client to reconnect.

*Note: The KeepAlive interval and Idle Timeout work independently and can be used separately or together.* 
 
  
 **Init Status Delay**  
 Specify time limits. This is the delay between the time when TN3270 service connects to a host session and the time the TN3270 service starts updating the client screen. There are often a large number of startup messages when the TN3270 service first connects to a host session, and this option gives the user the opportunity not to receive them all.  
  
 **Message Close Delay**  
 Specify time limits. When TN3270 service forces a client computer to disconnect (for example, when the Host Integration Server session to the host has been lost), it sends the client computer an error message to be displayed on the screen. This value specifies the time between sending the message to the client computer and closing the socket with the client computer (which causes some client computers to clear the screen, and so erase the message).  
  
 **Refresh Cycle Time**  
 Specify time limits. This is the delay between updates of the status on the display.  
  
 **Default RU Sizes - Inbound and Outbound**  
 This controls the RU size (SNA message size) used by the TN3270 service for logon messages to and from the host. The minimum value for inbound or outbound RU size is 256 bytes. If the host application sends large logon screens, these values should be increased.  
  
 **Certificate CN**  
 The common name of the certificate used if TLS/SSL is enabled.  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help1.md)