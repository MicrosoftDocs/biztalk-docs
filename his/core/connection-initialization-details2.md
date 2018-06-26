---
title: "Connection Initialization Details2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 143e294d-904a-44d7-a50b-3002cbfc45dc
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Connection Initialization Details
For an overview, refer to the topic [Connection Initialization Overview](../core/connection-initialization-overview1.md).  
  
## Step 1, outbound  
 When [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] attempts to activate a DLC connection, it first sends out an LLC TEST frame to the host's network adapter address to initiate the link level connection, and to verify the link station to link station transmission path.  
  
 This TEST command is sent by the SNADLC 802.2 link service through the Windows DLC driver.  
  
 Host Integration Server issues this TEST command at the start of every 802.2 connection. Although this command does not cause connection activation, its failure precludes continuing the activation.  
  
 This TEST command causes the remote link station to return a TEST Response. This will not affect the mode or state of the remote link station.  
  
 TOKEN-RING CONNECTIONS:  
  
 The TEST command is sent to the local ring first.  
  
 If Host Integration Server does not receive a reply to this TEST command within 0.5 seconds, it resends it, with the "all routes broadcast" setting enabled, causing it to be forwarded to adjacent rings by any source routing bridges which are present on the ring. The SNADLC link service will send a total of three all-routes broadcast TEST commands if the remote station (host) is not responding.  
  
 ETHERNET CONNECTIONS:  
  
 The TEST command does not contain any source-routing information.  
  
 Host Integration Server sends four TEST commands to the host's network adapter address.  
  
1.  802.3 to the regular MAC address  
  
2.  802.3 to the bit flipped MAC address  
  
3.  DIX format to the regular MAC address  
  
4.  DIX to the bit flipped MAC address  
  
## Step 2, inbound  
 The success of the TEST command indicates that the host's network interface adapter is accessible, and is configured for SNA communication.  
  
 The failure to receive a response to the TEST command will result in an Event 230 "No response to TEST commands".  
  
 What does this failure imply?  
  
1. The **Remote Network Address**, which is the host's network adapter address, is incorrectly configured on the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Connection Properties dialog box, Address Tab. It should match the **Local Adapter Address** defined in the AS/400 line description, or the **Switched Line** in the VTAM definition.  
  
2. Multiple Network Adapter Cards: If the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer has multiple network adapter cards, say one for the SNA Link Service, and the other for Windows domain connectivity, and the SNA Link Service is configured to communicate over the NT domain adapter, there obviously will be no AS/400 response.  
  
3. Intermediate bridges or routers are not passing the DLC Protocol between the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer and the host. DLC traffic cannot reach the segment or ring on which the AS/400's network address resides because the intermediate locater is not forwarding the LLC frames.  
  
4. The host is not enabled for SNA communication (this occurs rarely).  
  
## Step 3, outbound  
 Verify that the host's **LAN SSAP** matches the Host Integration Server **Remote SAP Address** property.  
  
 A NULL XID command is sent to the host. This is required as part of link level connection establishment. This command is sent to the host's **LAN SSAP** (which is referred to in the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] environment as the **Remote SAP Address**). This is the port that the host 'listens to', when receiving messages from the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer. SNA protocol uses a default **LAN SSAP** of 0x04.  
  
## Step 4, inbound  
 The success of the NULL XID command is indicated when Host Integration Server receives back a RQOS (Request Open Station) XID response.  
  
 The failure to receive a RQOS command will also result in the generation of an Event 230 – "No Response to XID Commands".  
  
 This indicates that the Host Integration Server timed out before the RQOS command was received, because:  
  
- The Host Integration Server **Remote SAP Address** was incorrect.  
  
- The AS/400 was unable to create a new APPC Controller for some reason. For example, AUTOCRTCTL is disabled.  
  
- The AS/400 APPC Controller or VTAM PU is in an Error State, or Inactive Status.  
  
  On Ethernet and Token-Ring networks, if the host does not reply to the XID command, then the connection remains in a pending condition, and an Event 230 will be logged in the NT Event Viewer Application log. The Host Integration Server computer will continually attempt connection startup, though only the first Event ID 230 will be logged with the Event Viewer, to prevent the log from filling up.  
  
## Step 5, outbound  
 Verify that the Host Integration Server computer's "Local Parameters" match an APPC Controller, or VTAM PU, description on the host.  
  
 An XID command is sent to the host. This XID contains the Host Integration Server computer's "Local Parameters". The parameters of interest are the Host Integration Server computer's network adapter address, "Local" **Network Name**, and "Local" **Control Point Name**.  
  
## Step 6, inbound  
 The success of the "Local Parameters" XID is indicated when Host Integration Server receives back a "Remote Parameters" XID from the host containing its "Local Parameters".  
  
 The failure to receive this "Remote Parameters" XID from the host will result in the generation of an Event 56 - "XID rejected by remote computer  
  
 The host failed to match the parameters sent in Step 5 to a known APPC controller or VTAM PU definition.  
  
 Host Integration Server logs Event 56 when it receives an XID Negotiation Error (X'22') Control Vector from the host. This control vector includes an offset pointer into the XID that was sent to the host in Step 5, where the offset points to the parameter in error. If the offset is "2" (pointing to the Local Node ID parameter), then an Event 47 is logged. If the offset is 19 (pointing to the link role parameter), then an Event 46 is logged. These two events are very rare. If some other offset is received (99.9% of the time), then Event 56 is logged.  
  
 For the purpose of discussion, lets assume an APPC Controller already exists on the host containing:  
  
- The address of the network adapter in the Host Integration Server computer, which is referred to on the AS/400 as the **LAN remote adapter address** (ADPTADR).  
  
- A specific **Remote network identifier** (for example, APPN).  
  
- A specific **Remote control point** (for example, TEST1).  
  
  The XID sent in step 5 will be rejected under the following circumstances:  
  
1. There is already an APPC controller defined on the AS/400 with the same name as the name defined in [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] SNA Manager, but it has a different **LAN remote adapter address** (ADPTADR)" associated with it.  
  
    Another way of saying the same thing is: The Host Integration Server computer attempted to connect with an invalid **"Local" Network Name**. For example: ESSLAB, where the AS/400 was expecting APPN.  
  
    (There is a source of potential confusion here. The **Remote Network Identifier** in the APPC Controller description corresponds to the **"Local" Network Name** on the Host Integration Server **Connection Properties** dialog box, **System** tab. However, on the AS/400 Display Networks Attributes screen, you will very likely see that the value for the **Local network ID** is identical to the APPC **Remote Network Identifier**. The confusion exists because the Host Integration Server **"Local" Network Name** is apparently referred to by two different field names on the AS/400. However, these two AS/400 fields *are not* the same. The AS/400 **Remote Network Identifier** *must* match the Host Integration Server **"Local" Network Name.** The AS/400 **Local network ID** does not have to match. It is usually defaulted to the same name as the **Remote Network Identifier** for the sake of convenience, however, the name actually refers to the AS/400's "local" network ID, *not* the "local" network name on Host Integration Server).  
  
2. There is already a different controller name defined on the AS/400 with the same "**LAN remote adapter address** (ADPTADR)" (Autocreate Controller (AUTOCRTCTL) is set to YES in the AS/400 Line Description).  
  
    In other words, The Host Integration Server computer attempted to connect with an invalid **"Local" Control Point Name**. For example: TESTXXX, where the AS/400 was expecting TEST1.  
  
3. The **Remote Control Point Name** in the Host Integration Server **Connection Properties** dialog box does not match the **Local Control Point Name** in the AS/400 Network Attributes screen.  
  
4. The Host Integration Server computer is configured with XID Type: Format 0, when the AS/400 requires XID Type: Format 3.  
  
## Step 7  
 [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] uses a four-step algorithm to match the hosts "Local parameters". If a step succeeds, any remaining steps are bypassed, and the activation sequence continues to step 8.  
  
1. The **Network Name** and **Control Point Name** from the host XID are compared to the **Network Name** and **Control Point Name** in the "Remote" Node Name section of the Host Integration Server **Connection Properties** dialog box, **System Identification** tab.  
  
2. If the host XID does not contain a network name and control point name (format 0 XID) or those fields are blank in the Host Integration Server **Connection Properties** dialog box, the matching will proceed to the next step. If the comparison fails, the XID will be rejected and event ID 49 is generated. If the comparison is successful, the XID will be responded to in step 8.  
  
3. If Host Integration Server is unable to match the **Network Name** and **Control Point Name**, it will compare the IDBLK and IDNUM (Node ID) in the XID to the "Remote" Node ID field in the Host Integration Server **Connection Properties** dialog box. If this field is blank, the matching will proceed to the next step. If the comparison fails the XID is rejected and NT Event ID 49 is generated.  
  
   > [!NOTE]
   >  All XIDs must contain an IDBLK and IDNUM.  
  
    If the comparison is successful, the XID will be responded to in step 8.  
  
4. Host Integration Server then compares the network address contained within the incoming XID to the **Remote Network Address** configured in the Host Integration Server **Connection Properties** dialog box. For x.25 the Remote X.25 address is used. If this comparison fails, the XID is rejected and NT Event ID 49 is generated. For SDLC the XID is simply accepted.  
  
   If the comparison process fails, an Event 49 is generated by Host Integration Server, and logged with the NT Event Service.  
  
## Step 8  
 The connection eventually goes active.