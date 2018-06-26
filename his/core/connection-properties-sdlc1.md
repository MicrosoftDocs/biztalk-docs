---
title: "Connection Properties: SDLC1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_PU_SDLC"
ms.assetid: 98b1d149-cf20-4ccb-8997-26fa2be4a6b2
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Connection Properties: SDLC
The following tabs are available on the SDLC Connection Properties sheet:  
  
## Connection Properties: General  
 **Name**  
 Enter a Name.  
  
 **Link Service**  
 Select a link service from the drop down list. If the link service you want is not in the list, click **Cancel**.  
  
 **Comment**  
 Optionally, enter a comment of not more than 25 characters.  
  
 **Remote End**  
 Select the type of remote system for this connection:  
  
- Host System  
  
- Peer System  
  
- Downstream  
  
- PU Passthrough  
  
  If this connection will be used for 3270 or LUA LUs, then select Host System.  
  
  If you will be using dependent APPC, which relies on a host system for communications, then select Host System, not Peer System.  
  
  **Allowed Directions**  
  Select the allowed call direction(s), **Outgoing Calls** and/or **Incoming Calls**.  
  
  Selecting **Outgoing Calls** causes [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] to initiate the link-level connection to the remote system or host. If a remote system tries to initiate a connection, Host Integration Server will not accept the connection attempt.  
  
  Selecting **Incoming Calls** causes Host Integration Server to accept connection attempts from remote systems or hosts.  
  
  If both are selected, Host Integration Server will both initiate a connection and accept connection attempts by other systems.  
  
  When multiple SDLC connections all use the same link service, and the connections accept incoming calls, the encoding (**NRZ/NRZI**) settings for all the connections must match.  
  
  **Activation**  
  If **Outgoing Calls** are included in Allowed Directions, select an Activation setting:  
  
  **On Server Startup**. Select this option if you want the connection to be readily available whenever the server is started.  
  
  **On Demand**. Select this option if you want the connection to be started when needed, and stopped when not in use.  
  
  **By Administrator**. Select this option if you want the administrator to control the connection on a case-by-case basis.  
  
  **Passthrough via Connection**  
  Displays a list of available (unpaired) PU Passthrough Connections. Connections that have already been paired are not available. Choose a connection that will route you to your destination PU. If PU Passthrough is not selected in the Remote End field, this list is unavailable.  
  
  **Supports Dynamic Remote APPC LU Definition**  
  Automatically configures the APPC Remote LUs as users request them. This feature requires that an APPN End Node or Net Node be available on the connection. This feature is for convenience, and should not be used in situations of restricted access. If Host System or Peer System is not selected in the Remote End field, this option is unavailable.  
  
  With dynamic APPC configuration, if a user requests a session with a valid remote LU, the connection will be established even if the remote LU has not been configured in SNA Manager. If a connection is designated to support dynamic APPC configuration, Host Integration Server will automatically define a remote LU and partner it with a local LU when needed. However, to take advantage of session status and other features of Host Integration Server, it is recommended that administrators configure commonly used remote LUs.  
  
## Connection Properties: Address  
 **Dial Data**  
 If this connection uses a switched line and the phone number is not stored in the modem, enter the dial data. With a leased SDLC line, this field is unavailable.  
  
 For ways to supply a phone number to the modem, see Phone Number Storage and Modem Types below.  
  
 **Poll Address**  
 Type a two-digit hexadecimal number. Contact the administrator of the remote system to determine the appropriate value. If the remote system is a host, the local poll address should match the VTAM PU definition for the ADDR= parameter.  
  
 If the remote system is a peer, the poll address can be any value except the reserved values 00 and FF. When the connection is used, the link roles will be negotiable; the system that takes on the primary role uses the poll address of the other system, so that the poll addresses match during the session.  
  
> [!NOTE]
>  Do not use 00 or FF. These values are reserved.  
  
 **Encoding**  
 Select the encoding scheme for your modem to use.  
  
 Your modem must use the same encoding scheme as the modem at the remote computer.  
  
 One of two encoding methods for modems:  
  
- NRZ — Non-return to zero  
  
- NRZI — Non-return to zero inverted  
  
  For connections to host systems, the encoding scheme must match the NRZI setting in the LINE/GROUP definition in VTAM. Obtain this setting from the host administrator. If VTAM does not specify an NRZI setting, it defaults to NRZI=YES.  
  
  When multiple SDLC connections all use the same link service, and the connections accept incoming calls, the encoding (**NRZ/NRZI**) settings for all the connections must match.  
  
  **Phone Number Storage and Modem Types**  
  Host Integration Server can store a phone number and then send the number (in ASCII) to a modem, which dials the number. This requires that the modem be attached to an SDLC adapter with a built-in serial (COM) port (for example, the SDLC adapters from MicroGate).  
  
  Several connection parameters must be set to work with your modem: Dial Data the duplex setting, half-duplex or full-duplex, and the encoding scheme.  
  
  **Changing the Host Integration Server Dialing Method**  
  To change the Host Integration Server dialing method for a modem, use the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Link Service Setup program to modify the link service. Restart SNA Manager and, from the **File** menu, choose **Save Configuration**.  
  
  **Modem Requirements for Accepting a Phone Number from Host Integration Server**  
  To accept a phone number from Host Integration Server, your modem must be set up so that it will do the following:  
  
- Accept dial commands in ASCII (eight data bits, no parity bit, one stop bit).  
  
- Not dial when the DTR signal is raised.  
  
- Set Clear to Send (CTS) and Data Set Ready (DSR) to **On** when ready to accept dial commands.  
  
- Set DSR to **Off** after accepting a dial command.  
  
- Set DSR to **On** again when (and only when) the dialed connection is made.  
  
- Change to **Synchronous** mode after the dial-up has completed.  
  
- Change back to **Dial-command** mode if Data Terminal Ready (DTR) is dropped and raised again.  
  
  **Host Integration Server Actions When Sending a Phone Number**  
  When Host Integration Server is sending a phone number to a modem, it ignores modem responses and holds the modem interface signals Select Standby and DTR to **Off**.  
  
  The dialing attempt initiated by Host Integration Server is assumed to have failed if one of the following occurs:  
  
- DSR stays on after the dial string has been sent.  
  
- The connection time-out expires before DSR comes on to indicate that the call is connected.  
  
  When Host Integration Server creates a dial string to send to a modem, it uses the outgoing command string supplied in Setup as a base, and then appends the Dial Data (phone number) configured in SNA Manager, followed by a carriage-return line-feed sequence.  
  
  **Affiliate Application**  
  If you selected Single Sign-On, choose an Affiliate Application from the list. The Enterprise Single Sign-On (SSO) Affiliate applications are logical entities that represent a system or sub-system such as a host, back-end system, or line of business application to which you are connecting using SSO. An affiliate application can represent a back-end system such as a mainframe or UNIX computer. It can also represent an application such as SAP, or a subdivision of the system, such as the "Benefits" or "Pay stub" sub-systems.  
  
## Connection Properties: System ID  
  
### Local Node Name  
 **Network Name**  
 If you are instructed by the administrator of a remote host, peer, or downstream system, and if you are using Format 3 XIDs, type the Network Name of the remote system. Format 3 is the default XID type.  
  
 The Network Name works with the Control Point Name to identify a system. If either of these parameters is supplied, the other should also be supplied.  
  
 **Control Point Name**  
 If you are instructed to by the administrator of a remote host, peer, or downstream system, and if you are using Format 3 XIDs, type the Control Point Name of the remote system. Format 3 is the default XID type.  
  
 The Control Point Name works with the Network Name to identify a system. If either of these parameters is supplied, the other should also be supplied.  
  
 **Local Node ID**  
 If this connection uses a switched SDLC line (standard telephone line) to connect to a host system, type the Local Node ID. Use the same Local Node ID for all connections and link services on a particular server.  
  
 If this connection uses a leased SDLC line, you can use the default for the Local Node ID.  
  
> [!NOTE]
>  Do not use 000 or FFF for the first three digits; these values are reserved.  
  
 **XID Type**  
 Select the XID Type. Most systems use Format 3.  
  
 If you want to use independent APPC LUs on this connection, you must select Format 3.  
  
 When Host Integration Server is configured to use Format 0 over a host connection, the host treats it as a PU type 2.0, and so Host Integration Server exercises only its PU type 2.0 capabilities. When Host Integration Server establishes a host or peer connection using Format 3 and independent LUs, Host Integration Server exercises its PU type 2.1 capabilities.  
  
 For configuration changes to take effect, restart the server.  
  
### Remote Node Name  
 **Network Name (Remote Node)**  
 If you are instructed by the administrator of a remote host, peer, or downstream system, and if you are using Format 3 XIDs, type the Network Name of the remote system. Format 3 is the default XID type.  
  
 The Network Name works with the Control Point Name to identify a system. If either of these parameters is supplied, the other should also be supplied.  
  
 **Control Point Name (Remote Node)**  
 If you are instructed to by the administrator of a remote host, peer, or downstream system, and if you are using Format 3 XIDs, type the Control Point Name of the remote system. Format 3 is the default XID type.  
  
 The Control Point Name works with the Network Name to identify a system. If either of these parameters is supplied, the other should also be supplied.  
  
 **Remote Node ID**  
 If instructed to by the administrator of a remote host, peer, or downstream system, type the Remote Node ID.  
  
> [!NOTE]
>  Do not use 000 or FFF for the first three digits; these values are reserved.  
  
 **Peer DLC Role**  
 Select the DLC role for this connection. The options are:  
  
-   Primary  
  
-   Secondary  
  
-   Negotiable  
  
## Connection Properties: SDLC  
 **Max BTU Length**  
 Specify the Maximum Basic Transmission Unit (BTU) Length.  
  
 The range is from 265 through 16393; the default is **265**.  
  
 With an IBM SDLC adapter, set the Max BTU Length to 521 or less.  
  
 Maximum Basic Transmission Unit length. The maximum number of bytes that can be transmitted in a single data-link information frame. A BTU is sometimes called an I-frame.  
  
 For downstream connections, specify a Max BTU Length less than or equal to the maximum value supported by software on the downstream system.  
  
 For host connections, specify a Max BTU Length less than or equal to the VTAM PU definition for the MAXDATA= parameter.  
  
 **Data Rate**  
 Select the Data Rate.  
  
 The data rate for transmissions between the Host Integration Server communications adapter and the modem:  
  
- **Low** gives more reliable transmissions and prevents the transmission errors sometimes caused by poor-quality lines at the high rate. If a fall-back line speed setting is supported by your modem and communications adapter, and you want to enable it, select **Low**.  
  
- **High** gives faster transmissions. If you select **High**, the CCITT line 111 on the V24 interface of your modem is set to on.  
  
  Check your adapter and modem manuals to find out if the data rate can or must be set for your equipment.  
  
  **Duplex**  
  Select the setting that matches your modem:  
  
- For a half-duplex modem, select **Half**. If none of your adapters were installed with the Constant RTS option set, you can only choose half-duplex.  
  
- For a full-duplex modem, select **Full**. If you want to use the full-duplex setting, one or more of your adapters must have the Constant RTS option set (at installation).  
  
  Most servers will use the default, **Half**.  
  
  **Idle Timeout (for host or peer connections)**  
  Specify the length of time, in tenths of a second, for the local system to wait for a response to a transmission before trying again. Too small of a timeout can cause connection problems. This parameter affects sessions in which the server has a link role of secondary; therefore, it affects all sessions with a host system and some sessions with a peer system (where the link role is negotiable).  
  
  The range is from 1 (one-tenth of a second) through 300 (30 seconds). The default is **300** (30 seconds).  
  
  **Idle Retry Limit (for host or peer connections)**  
  Specify the number of times for the local system to try to send data to the remote system if there is no response. This parameter affects sessions in which the server has a link role of secondary; therefore, it affects all sessions with a host system and some sessions with a peer system (where the link role is negotiable).  
  
  The range is from 1 through 255; the default is **10**.  
  
  **Poll Rate**  
  If the remote system is a peer or downstream system, specify the **Poll Rate** (in polls per second).  
  
  The range is from 1 through 50 polls per second; the default is **5**.  
  
  **Poll Timeout (for peer or downstream connections)**  
  Specify the length of time, in tenths of a second, for the local system to wait for a response to a poll before trying again. Too small of a timeout can cause connection problems. This parameter affects sessions in which the server has a link role of primary; therefore, it affects all sessions with a downstream system and some sessions with a peer system (where the link role is negotiable).  
  
  The range is from 1 (one-tenth of a second) through 300 (30 seconds). The default is **10** (1 second).  
  
  **Poll Retry Limit (for peer or downstream connections)**  
  Specify the number of times for the local system to poll the remote system if there is no response. This parameter affects sessions in which the server has a link role of primary, therefore, it affects all sessions with a downstream system and some sessions with a peer system (where the link role is negotiable).  
  
  The range is from 1 through 255; the default is **10**.  
  
  **Select Standby**  
  If you want your modem's Standby line to be set to on, select this check box.  
  
  Check your adapter and modem manuals to find out if standby can be set for your equipment.  
  
  **Multidrop Primary**  
  If this is a leased SDLC line to downstream systems, and this server will be the primary station for a multidrop connection, then select this box.  
  
  This is a connection through which one primary computer simultaneously communicates with multiple secondary computers. [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] supports multidrop connections to peer or downstream systems on leased SDLC lines.  
  
  **Contact Timeout**  
  Specify the length of time, in tenths of a second, which the SDLC link service waits for an XID or SNRM response before resending the XID or SNRM.  
  
  This parameter is ignored for incoming calls.  
  
  The range is from 5 (five-tenths of a second) through 300 (30 seconds).  
  
  The default for a host connection is 300 (30 seconds). The default for a peer or downstream connection is 10 (1 second).  
  
  **Contact Retry Limit**  
  Specify the maximum number of times the link service will resend an XID or SNRM before declaring an outage to Host Integration Server.  
  
  This parameter is ignored for incoming calls.  
  
  The range is from 1 through 20; the default is **10**.  
  
  **Connection Dialing Timeout**  
  If this connection uses a switched SDLC line (standard telephone line), specify the number of seconds that will be allowed for the user or modem to dial and make a connection to the remote computer. If the dialing will be done manually, be sure to allow enough time for the user to dial, wait for an answer, and make the connection.  
  
  The range is from 10 through 500 seconds; the default is **300**.  
  
  This parameter is ignored by incoming calls.  
  
  To exit the dialog box without accepting the configuration settings, click **Cancel**. To accept the settings, click **OK**.  
  
  To put configuration changes into effect, restart the server.  
  
  **Connection Retry Limits**  
  Supply activation limits for the connection.  
  
  **Maximum Retries**  
  Select the number of attempts for Host Integration Server to make when trying to establish the connection. After making this number of attempts, Host Integration Server makes an entry in the event log and stops trying. The range is from 1 through No Limit; the default is **No Limit**.  
  
  **Delay After Failure**  
  Select the length of time for Host Integration Server to wait between attempts to establish the connection. The range is from 5 seconds through 255 seconds; the default is **10** seconds.  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help1.md)