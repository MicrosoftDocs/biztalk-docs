---
title: "Troubleshooting SDLC Connections1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb5357cc-31f6-41a6-8385-9416eeebe299
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Troubleshooting SDLC Connections
To begin troubleshooting an SDLC connection, it is helpful to look at two simple indicators of activity: the server and connection status shown in SNA Manager, and the modem lights. Event logs also provide important information. The following table outlines some ways to interpret symptoms of a nonfunctioning SDLC connection.  
  
|Symptom|Configuration item to check|  
|-------------|---------------------------------|  
|**Symptom**: [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] will not start; the System Event Log (viewable through the Event Viewer) contains messages about a link service failing to start.|**Recommendation**: Check that all existing link services are configured to work with functioning adapters. The SNA Manager service cannot start if any existing link service cannot start, even if that link service is not being used by any connection.|  
|**Symptom**: [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] will not start; System Event Log contains messages about conflicts in port addresses, IRQs, or DMA addresses.|**Recommendation**: Check the port address, IRQ setting, or DMA channel of the SDLC adapter, which may be conflicting with those of another adapter (for example, a sound system adapter) or port in your computer. Change the settings on one of the adapters or ports, if possible, or remove the conflicting adapter. For more information, see [SDLC Adapters and Link Services: Installation Pointers](../core/sdlc-adapters-and-link-services-installation-pointers.md).|  
|**Symptom**: Modem lights may flash but the connection remains at "Pending" and does not go to "Active."|**Recommendation**: Check the DMA channel setting (jumpers) on the adapter and compare this to the setting in the link service properties dialog box. If this setting specifies a nonexistent address, data cannot flow.|  
|**Symptom**: Modem appears to make the connection ("receive data" light flashes, but "transmit data" light does not). The connection status reaches "Pending" and then the connection is dropped.|**Recommendation**: Check the cables; then check the Encoding (NRZ/NRZI) setting used by the host and compare this to the setting in the connection properties dialog box. If the NRZ/NRZI settings do not match, the two ends of the connection begin negotiating but cannot interpret each others signals correctly. For more information, see the preceding section.|  
|**Symptom**: Modem lights are flashing but the connection can only reach "Pending" status. Also, the Application Event Log contains event 182.|**Recommendation**: Check that the identifiers (IDs or names) used by the host match the ones used in the **Connection Properties** dialog box. If the identifiers do not match, the exchange ID (XID) process cannot complete successfully. For more information about identifiers, see [Settings to Check for All Connection Types](../core/settings-to-check-for-all-connection-types.md).|  
|**Symptom**: Connection (especially downstream connection) may become "Active," but reverts to "Pending" when first user attempts to start a session.|**Recommendation**: Check the Max BTU Length setting in the **Connection Properties** dialog box. For details about the correct setting to use, see the preceding section.|  
  
 If one or more 3270 LUs never becomes active, even when users are attempting to start sessions, the LOCADDR settings in the LU definitions in VTAM or NCP may not match the Host Integration Server LU numbers, or some or all of the LUs may be inactivated in VTAM or NCP. To correct this, consult with the administrator of the host system.