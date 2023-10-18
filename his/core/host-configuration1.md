---
description: "Learn more about: Host Configuration"
title: "Host Configuration1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_PU_8022"
ms.assetid: 5f2555f5-3e47-420b-994b-d3843348fba8
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Host Configuration
For a connection to be established successfully between a host computer and a [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer, a number of software configuration settings (VTAM, NCP, or AS/400), and hardware characteristics must work together. These include the mainframe node ID settings, AS/400 name settings, addresses, BTU length, and link service settings.  

 The following table provides more details about important configuration items.  


|                                                                                                    Element                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Important items to consider                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Host configuration** settings (VTAM, NCP, or AS/400 settings) must match the **Connection and Server** settings on [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]       | **Mainframe Node ID settings:** For most mainframes, IDBLK and IDNUM in the PU definition must be matched by the two parts of the Remote Node ID on the Host Integration Server connection.<br /><br /> **AS/400 name settings:** For the AS/400, local and remote Control Point Names (CP names) and network names must match corresponding Host Integration Server settings (local names configured on the server and remote names on the connection).<br /><br /> **BTU length:** For the mainframe, this is set through MAXDATA in the PU definition. For the AS/400, this is set through MAXFRAME. These should equal the Max BTU Length on the Host Integration Server connection.<br /><br /> **Other settings:** For some connections, other settings are also important. For example, for Synchronous Data Link Control (SDLC), the NRZ/NRZI settings on the host must match those on the Host Integration Server connection. For details about these and other settings, see the section about the type of connection you are configuring. |

 When you are configuring a new host connection or troubleshooting an existing connection, regardless of the connection type, the identifiers between the host and Host Integration Server must match. The following sections describe various configuration settings.  

## In This Section

 [Mainframe Connections with XIDs](../core/mainframe-connections-with-xids1.md)  

 [Mainframe Connections without XIDs](../core/mainframe-connections-without-xids2.md)  

 [i Series Connections](../core/as-400-connections1.md)  

 [Configuring VTAM for 3270 Access](../core/configuring-vtam-for-3270-access1.md)  

 [Sample VTAM Parameters](../core/sample-vtam-parameters1.md)  

 [Configuring VTAM for APPC Access](../core/configuring-vtam-for-appc-access1.md)  

 [Sample CICS Configuration Screens for Use with APPC](../core/sample-cics-configuration-screens-for-use-with-appc2.md)  

 [Configuring NCP for Independent APPC](../core/configuring-ncp-for-independent-appc1.md)  

 [Configuring the AS/400 for 5250 Access](../core/configuring-the-as-400-for-5250-access2.md)  

 [Table of Parameters for AS/400 Communication](../core/table-of-parameters-for-as-400-communication1.md)
