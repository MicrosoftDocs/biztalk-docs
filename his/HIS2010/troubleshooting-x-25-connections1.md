---
title: "Troubleshooting X.25 Connections1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7abc5c73-9ca5-449d-b4b3-e5fb090b0fcb
caps.latest.revision: 4
---
# Troubleshooting X.25 Connections
The following table outlines some ways to interpret symptoms of a nonfunctioning X.25 connection.  
  
|Symptom|Configuration item to check|  
|-------------|---------------------------------|  
|**Symptom**: [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will not start; the System Event Log (viewable through the Event Viewer) contains messages about a link service failing to start.|**Recommendation**: Check that all existing link services are configured to work with functioning adapters. The SNA Manager cannot start if any existing link service cannot start, even if that link service is not being used by any connection.|  
|**Symptom**: Host Integration Server will not start; System Event Log contains messages about conflicts in port addresses, IRQs, or DMA addresses.|**Recommendation**: Check the port address, IRQ setting, or DMA address of your X.25 adapter, which may be conflicting with those of another adapter or port in your computer. Change the settings on one of the adapters or ports, if possible, or remove the conflicting adapter. For more information, see [X.25 Adapters and Link Services: Installation Pointers](../HIS2010/x-25-adapters-and-link-services-installation-pointers2.md).|  
|**Symptom**: Connection can only reach "Pending" status, and the Application Event Log contains Event 23 with an outage code of 0x62 (for SVC) or 0x61 (for PVC).|**Recommendation**: Check that the identifiers (IDs or names) and/or the X.25 address used by the host match the corresponding parameters on the **System Identification** tab of the **Connection Properties** dialog box. The identifiers or addresses must match in order for the exchange of identifiers (XIDs) and test frames to complete successfully. For more information about identifiers, see the preceding section and [Settings to Check for All Connection Types](../HIS2010/settings-to-check-for-all-connection-types1.md).|  
|**Symptom**: Connection (especially downstream connection) may become "Active," but reverts to "Pending" when first user attempts to start a session.|**Recommendation**: Check the **Max BTU Length** setting for the connection on the **X.25** tab of the **Connection Properties** dialog box. For details about the correct setting to use, see the preceding section.|  
  
 If one or more 3270 LUs never becomes active, even when users are attempting to start sessions, the LOCADDR settings in the LU definitions in VTAM or NCP may not match the Host Integration Server LU numbers, or some or all of the LUs may be inactivated in VTAM or NCP. To correct this, consult with the administrator of the host system.