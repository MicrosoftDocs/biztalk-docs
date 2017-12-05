---
title: "LU6.2 Tab (Remote Environment Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15214"
ms.assetid: 835ea850-19e4-4ebc-9014-28ecdc4f0e9f
caps.latest.revision: 4
---
# LU6.2 Tab (Remote Environment Properties)
Use the **LU 6.2** tab to define the network characteristics that the Windows environment uses to interact with the host.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Local LU alias**|Select a local LU alias from the drop-down list, or type the alias to be used by this remote environment when contacting the mainframe. Create and configure this local LU alias through SNA Management (SNA Server)/SNA Manager (Host Integration Server) before you use the remote environment. The LU identified by the alias must correspond with a VTAM independent LU on the mainframe.<br /><br /> The alias can be a maximum of 256 alphanumeric characters. The drop-down list displays all the local APPC LUs defined to the SNA Manager.|  
|**Remote LU alias**|Select a remote LU alias from the drop-down list, or type the alias to be used by this remote environment when contacting the mainframe. Create and configure this remote LU alias through SNA Management before you use the remote environment. The partner LU identified by this alias must identify the ACBNAME of the CICS region, the partner LU associated between APPCMVS and IMS to reach IMS.<br /><br /> The alias can be a maximum of 256 alphanumeric characters. The drop-down list displays all the remote APPC LUs defined to the SNA Manager.|  
|**Mode name**|Select a mode name from the drop-down list, or enter the mode name to be used by this remote environment for sessions established with the mainframe. Create and configure this mode name through Host Integration Server SNA Manager before you use the remote environment. Ensure that a compatible mode has been defined on the mainframe. You can also obtain a list of configured modes from Host Integration Server **SNA Manager**. **Note:**  To use two-phase commit, the APPC mode must be Sync Level 2 capable.|  
|**Supports Sync Level 2 protocols**|Select this option to enable Sync Level 2 protocols for this remote environment.|  
|**Time-out in seconds**|View the time-out information used by the WIP runtime environment when it communicates with the host environment. The time-out values are used on transport-specific APIs to terminate the receive API function when no host data or acknowledgement is received in the specified amount of time.<br /><br /> When a remote environment is first created, no timeout value is specified. The TI run-time environment will wait indefinitely for the mainframe transaction program to return output parameters and simultaneously block the calling client application until this response is received. This blocking behavior is typical for APPC applications. To avoid indefinite blocking, set a timeout value in the **Receive** box.|  
|**Receive**|Type the number of seconds. The number of seconds can be a maximum of 3600 and a minimum of 0.|  
  
> [!CAUTION]
>  The properties of a remote environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the remote environment to function incorrectly.  
  
## See Also  
 [Remote Environments Node](../core/remote-environments-node1.md)   
 [Remote Environment Node](../core/remote-environment-node2.md)   
 [CICS Tab (for LU6.2 Link Properties)](../core/cics-tab-for-lu6-2-link-properties-1.md)   
 [TI Manager Properties](../core/ti-manager-properties1.md)