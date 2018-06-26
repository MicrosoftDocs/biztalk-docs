---
title: "Configuring NCP for Independent APPC1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 15ff08c8-ffae-42de-b9fd-321194518ba8
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuring NCP for Independent APPC
Parameters on Network Control Program (NCP) must match Advanced Program-to-Program Communications (APPC) parameters on [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]. To configure the needed parameters, consult with the host administrator for the matching NCP parameters.  
  
 This section provides information about NCP definitions used for supporting and defining independent LUs. The section is not intended to provide comprehensive information about NCP, which is described more thoroughly in IBM manuals such as:  
  
- *Planning and Reference for NetView, NCP, VTAM* (CN4D1200)  
  
- *NCP, SSP, and EP Resource Definition Guide* (CXDG7200)  
  
- *NCP, SSP, and EP Resource Definition Reference* (CXDH1200)  
  
  You may need to study other IBM documentation as well. Some of the topics to study are:  
  
- Independent LUs  
  
- Type 2.1 node support  
  
- Dynamic reconfiguration  
  
## Table of NCP Parameters That Affect Independent APPC  
 The following table shows basic recommendations for setting NCP parameters for independent APPC with Host Integration Server. The next sections describe the parameters in more detail.  
  
|NCP definition|NCP parameter|Recommendations|  
|--------------------|-------------------|---------------------|  
|BUILD|ADDSESS|Must support the number of sessions needed.|  
|Not applicable|AUXADDR|Must support the number of additional addresses needed.|  
|Not applicable|MAXSESS|Use for setting the maximum sessions allowed for any LU. Corresponds to the sum of all the parallel session limits for all the modes with which a particular LU is partnered.|  
|PUDRPOOL|NUMBER|Must support the number of servers accessing NCP.|  
|LUDRPOOL|NUMILU|Must support the number of dynamically configurable LUs needed.|  
|PU|NETID|Corresponds to the Local Network Name on Host Integration Server.|  
|Not applicable|PUTYPE|For independent APPC, use PUTYPE=2.|  
|Not applicable|XID|For independent APPC, use XID=YES.|  
|LU|LOCADDR|For independent LUs with set definitions, use LOCADDR=0.|  
|Not applicable|PACING|Use a value greater than or equal to the corresponding Host Integration Server parameter, the Pacing Receive Count in the mode.|  
|Not applicable|VPACING|Use a value less than or equal to the corresponding Host Integration Server parameter, the Pacing Send Count in the mode.|  
  
## BUILD Definition  
 The following parameters in the BUILD definition affect independent APPC:  
  
 **ADDSESS=** *value*  
 Is equivalent to the total number of sessions available to independent LUs. ADDSESS specifies the number of LU-LU session control blocks available for independent LUs. Note that session control blocks may be reserved for a particular LU by using RESSCB (reserved session control blocks) in the LU definition.  
  
 The sum of ADDSESS, AUXADDR, and NUMILU equals the total number of control blocks available for dynamic configuration of LUs. (For a description, see LUDRPOOL Definition, later in this topic.) This total should be high enough to support needed sessions, but low enough so that NCP does not exceed the storage capacity of the controller.  
  
 **AUXADDR=** *value*  
 Specifies the number of addresses that can be dynamically defined for both dependent and independent LUs. To allow for additional sessions between independent LUs, AUXADDR should be greater than ADDSESS. For more information about dynamic reconfiguration, see ADDSESS (the preceding description).  
  
 **MAXSESS=** *value*  
 Specifies the maximum number of LU-LU sessions that one independent LU can support. If you specify MAXSESS in an LU definition (as supported by NCP V6R2), the LU uses the value in the LU definition, not the BUILD definition. The limit set by MAXSESS prevents an independent LU from using too many unreserved session control blocks.  
  
## PUDRPOOL Definition  
 The following parameter in the PUDRPOOL definition affects independent APPC:  
  
 **NUMBER=** *value*  
 Specifies the number of physical units (PUs) that can be dynamically defined.  
  
## LUDRPOOL Definition  
 The following parameter in the LUDRPOOL definition affects independent APPC:  
  
 **NUMILU**= *value*  
 Specifies the number of independent LUs that can be added through dynamic reconfiguration. Find a value high enough to support needed sessions (including control-session overhead for parallel sessions), but low enough so that NCP does not exceed the storage capacity of the controller. Note that total LUs allowed by NUMILU plus NUMTYP1 plus NUMTYP2 is limited. The exact limit depends on your version of NCP.  
  
## PU Definition  
 The following parameters in the PU definition affect independent APPC:  
  
 **NETID=** *name*  
 Specifies the name of an adjacent network, and corresponds to the local Network Name on Host Integration Server. NETID allows the network names to differ between the host and Host Integration Server. This name is used in exchange identification (XID) negotiation.  
  
 **PUTYPE=2**  
 For independent APPC, use PUTYPE=2. When combined with XID=YES, this is equivalent to physical unit type 2.1.  
  
 **XID=YES**  
 For independent APPC, specify XID=YES, so that XIDs can be exchanged while in Normal Disconnected Mode (NDM).  
  
## LU Definition  
 The following parameters in the LU definition affect independent APPC:  
  
 **LOCADDR=0**  
 For independent LUs configured by an administrator (as contrasted with LUs dynamically configured by NCP), specify LOCADDR=0.  
  
 **PACING=** *value*  
 Specifies the number of frames for NCP to send to an independent LU before NCP waits for a pacing response. The value for PACING should generally be greater than or equal to the corresponding Host Integration Server mode parameter, Pacing Receive Count. This ensures a smooth flow of data from the host to the Host Integration Server. ([!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] does not support adaptive pacing.)  
  
 **VPACING=** *value*  
 Specifies the number of frames for NCP to receive from an independent LU before NCP sends a pacing response; sometimes called the receive window size. The value for VPACING should generally be less than or equal to the corresponding Host Integration Server mode parameter, Pacing Send Count. This prevents delays in sending from the Host Integration Server to the host. ([!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] does not support adaptive pacing.)  
  
## See Also  
 [Sample VTAM Parameters](../core/sample-vtam-parameters1.md)