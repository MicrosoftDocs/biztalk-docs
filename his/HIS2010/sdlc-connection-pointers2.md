---
title: "SDLC Connection Pointers2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0581b329-be30-41aa-a09a-212a499a241a
caps.latest.revision: 4
---
# SDLC Connection Pointers
Connections are configured through the SNA Manager. The steps for configuring an SDLC connection are described in detail in [Important Connection Information](../HIS2010/important-connection-information1.md). The following pointers indicate items that require special attention:  
  
 As with all connections, the settings must be configured correctly. For details, see [Settings to Check for All Connection Types](../HIS2010/settings-to-check-for-all-connection-types1.md).  
  
 If possible, configure the connection to use constant RTS. See the recommendations in [SDLC Adapters and Link Services: Installation Pointers](../HIS2010/sdlc-adapters-and-link-services-installation-pointers1.md).  
  
 The duplex setting is found in the **SDLC** tab of **SDLC Connection Properties**. Duplex can be half or full; the setting must not exceed the capabilities of the adapter and modem. For more information about the factors to consider when choosing the setting for duplex, see the preceding section.  
  
 Check the encoding setting, which is either nonreturn to zero (NRZ) or nonreturn to zero inverted (NRZI). The setting is on the **Address** tab of **SDLC Connection Properties**. This setting must match the equivalent setting on the host. For connections to mainframes, the NRZI setting is found in the LINE/GROUP definition in VTAM or NCP. (If VTAM does not specify the NRZI setting, it defaults to NRZI=YES.). For connections to AS/400 computers, the NRZI setting is in the Line Description.  
  
 When multiple SDLC connections accept incoming calls and use the same link service, the encoding (NRZ/NRZI) settings for all the connections must match.  
  
 Check the Max BTU Length setting, found on the **SDLC** tab of the **SDLC Connection Properties** dialog box. A BTU is also called an I-frame; it is the number of bytes that can be transmitted in a single data-link information frame.  
  
 Set the Max BTU Length so that it matches the capacity of the adapter and the host or downstream system. Otherwise, when the mainframe or AS/400 sends a logon screen (typically a full screen), the BTU length (frame size) that is used will be unworkable, causing the connection to be dropped. The following table provides guidelines:  
  
|For...|Set the Max BTU Length to...|  
|------------|----------------------------------|  
|IBM SDLC adapter|521 or less.|  
|Connection to a mainframe|Equal to MAXDATA in the PU definition on the mainframe (recommended).|  
|Connection to an AS/400|Equal to MAXFRAME on the AS/400 (recommended).|  
|Connection to a downstream system|Less than or equal to the maximum value supported by the downstream system.|  
  
 Setting the Max BTU Length correctly is especially important for downstream connections.  
  
 With SDLC connections, you can adjust a variety of other settings, especially timeout and retry settings. However, the defaults for the time-outs and retries are appropriate for most networks. Therefore, it is recommended that you do not adjust these settings unless you have a specific reason for doing so, and you understand the characteristics of your communications lines as well as the way that the time-outs work.