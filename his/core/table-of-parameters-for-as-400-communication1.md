---
description: "Learn more about: Table of Parameters for IBM System i Communication"
title: "Table of Parameters for AS-400 Communication1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Table of Parameters for IBM System i Communication
The following table summarizes details about configuring [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] for the IBM System i environment. In addition, for an X.25 connection using permanent virtual circuit (PVC), specify the PVC Alias.  
  
|SNA<br /><br /> Server<br /><br /> element|Parameter<br /><br /> name in<br /><br /> Host Integration Server|Instructions for configuring<br /><br /> for the IBM System i environment|  
|--------------------------------|-------------------------------------------------------|------------------------------------------------------------------|  
|Server|Network Name  (Local Node)|This generally corresponds to the RMTNETID setting on the IBM System i. (APPN is often used.)|  
|Server|Control Point Name  (Local Node)|Corresponds to RMTCPNAME on the IBM System i.|  
|Connection|Remote End|Select Peer System as the Remote End for the connection.|  
|Connection|Activation|Coordinate with the switched disconnect (SWTDSC) setting on the IBM System i. If SWTDSC is *YES, select On Demand. If SWTDSC is \*NO, select On Server Startup.|  
|Connection|Local Node ID|Specify the Local Node ID, a required parameter for all connections. This corresponds to EXCHID on the IBM System i.|  
|Connection|Control Point Name (Remote Node)|Specify the IBM System i Control Point Name (CP name) as the remote Control Point Name for the connection.|  
|Connection|Network Name (Remote Node)|Corresponds to the RMTNETID on the IBM System i. (APPN is often used.)|  
|Connection|Max BTU Length|Corresponds to the MAXFRAME setting on the IBM System i.|  
|Remote APPC LU|LU Name|Specify the Control Point Name of the IBM System i as the remote LU name.|  
|Mode|Mode name|Choose the QPCSUPP mode for all LU-LU pairs to be used for IBM System i connectivity.|  
|User or group listing|Default local  APPC LU|Assign a Default local APPC LU to the user or group. If the user or group does not specify a local LU name when opening a session to an IBM System i, this default local LU name will be used.|  
|User or group listing|Default remote APPC LU|Assign a Default remote APPC LU  which is the same as a default IBM System i  to the user or group. If the user or group does not specify a remote LU (that is, an IBM System i) when opening a session, the assigned IBM System i will be used.|  
  
## See Also  
 [Sample VTAM Parameters](../core/sample-vtam-parameters1.md)
