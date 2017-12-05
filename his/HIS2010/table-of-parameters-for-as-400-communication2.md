---
title: "Table of Parameters for AS-400 Communication2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12509d26-342a-49fb-82ac-e67f12bb5096
caps.latest.revision: 3
---
# Table of Parameters for AS/400 Communication
The following table summarizes details about configuring [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] for the AS/400 environment. In addition, for an X.25 connection using permanent virtual circuit (PVC), specify the PVC Alias.  
  
|SNA<br /><br /> Server<br /><br /> element|Parameter<br /><br /> name in<br /><br /> Host Integration Server|Instructions for configuring<br /><br /> for the AS/400 environment|  
|--------------------------------|-------------------------------------------------------|------------------------------------------------------------------|  
|Server|Network Name  (Local Node)|This generally corresponds to the RMTNETID setting on the AS/400. (APPN is often used.)|  
|Server|Control Point Name  (Local Node)|Corresponds to RMTCPNAME on the AS/400.|  
|Connection|Remote End|Select Peer System as the Remote End for the connection.|  
|Connection|Activation|Coordinate with the switched disconnect (SWTDSC) setting on the AS/400. If SWTDSC is *YES, select On Demand. If SWTDSC is \*NO, select On Server Startup.|  
|Connection|Local Node ID|Specify the Local Node ID, a required parameter for all connections. This corresponds to EXCHID on the AS/400.|  
|Connection|Control Point Name (Remote Node)|Specify the AS/400 Control Point Name (CP name) as the remote Control Point Name for the connection.|  
|Connection|Network Name (Remote Node)|Corresponds to the RMTNETID on the AS/400. (APPN is often used.)|  
|Connection|802.2: Remote Network Address<br /><br /> SDLC: Poll Address<br /><br /> X.25: Remote X.25 Address|Corresponds to ADPTADR in the Line Description on the AS/400.<br /><br /> Corresponds to STNADR in the Line Description on the AS/400.<br /><br /> Specify the address of the AS/400.|  
|Connection|Max BTU Length|Corresponds to the MAXFRAME setting on the AS/400.|  
|Remote APPC LU|LU Name|Specify the Control Point Name of the AS/400 as the remote LU name.|  
|Mode|Mode name|Choose the QPCSUPP mode for all LU-LU pairs to be used for AS/400 connectivity.|  
|User or group listing|Default local  APPC LU|Assign a Default local APPC LU to the user or group. If the user or group does not specify a local LU name when opening a session to an AS/400, this default local LU name will be used.|  
|User or group listing|Default remote APPC LU|Assign a Default remote APPC LU  which is the same as a default AS/400  to the user or group. If the user or group does not specify a remote LU (that is, an AS/400) when opening a session, the assigned AS/400 will be used.|  
  
## See Also  
 [Sample VTAM Parameters](../HIS2010/sample-vtam-parameters2.md)