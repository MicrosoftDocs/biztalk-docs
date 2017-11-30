---
title: "Host Configuration2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cf72866-ee7a-4c02-b31b-e96a1dd7c61d
caps.latest.revision: 4
---
# Host Configuration
For a connection to be established successfully between a host computer and a [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer, a number of software configuration settings (VTAM, NCP, or AS/400), and hardware characteristics must work together. These include the mainframe node ID settings, AS/400 name settings, addresses, BTU length, and link service settings.  
  
 The following table provides more details about important configuration items.  
  
|Element|Important items to consider|  
|-------------|---------------------------------|  
|**Host configuration** settings (VTAM, NCP, or AS/400 settings) must match the **Connection and Server** settings on [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]|**Mainframe Node ID settings:** For most mainframes, IDBLK and IDNUM in the PU definition must be matched by the two parts of the Remote Node ID on the Host Integration Server connection.<br /><br /> **AS/400 name settings:** For the AS/400, local and remote Control Point Names (CP names) and network names must match corresponding Host Integration Server settings (local names configured on the server and remote names on the connection).<br /><br /> **Addresses:** For several connection types (802.2, X.25, and channel), host settings must be matched with equivalent settings on the Host Integration Server connection. For details, see the section about the type of connection you are configuring.<br /><br /> **BTU length:** For the mainframe, this is set through MAXDATA in the PU definition. For the AS/400, this is set through MAXFRAME. These should equal the Max BTU Length on the Host Integration Server connection.<br /><br /> **Other settings:** For some connections, other settings are also important. For example, for Synchronous Data Link Control (SDLC), the NRZ/NRZI settings on the host must match those on the Host Integration Server connection. For details about these and other settings, see the section about the type of connection you are configuring.|  
|**For SDLC and X.25**<br /><br /> **Communications hardware:** line, modem (if applicable), and adapter characteristics must match the **Link service and connection** settings on the Host Integration Server|**Speed and duplexing:** For SDLC and X.25, note the speed and duplexing capabilities of the line, modem (or DCE), and adapter, and make sure that they will not be exceeded by the settings in the Host Integration Server link service and connection. Settings for fast transmission or for full duplexing cause greater demands on hardware. (Fast transmission plus full duplexing cause the greatest demands.) The hardware element with the smallest capacity will limit the capacity of the entire system. For example, with an SDLC adapter that lacks a coprocessor, you cannot use full-duplex transmissions at high speeds, even if the modem and line can handle them.|  
  
 When you are configuring a new host connection or troubleshooting an existing connection, regardless of the connection type, the identifiers between the host and Host Integration Server must match. The following sections describe various configuration settings.  
  
## In This Section  
 [Mainframe Connections with XIDs](../HIS2010/mainframe-connections-with-xids2.md)  
  
 [Mainframe Connections without XIDs](../HIS2010/mainframe-connections-without-xids1.md)  
  
 [AS/400 Connections](../HIS2010/as-400-connections2.md)  
  
 [Configuring VTAM for 3270 Access](../HIS2010/configuring-vtam-for-3270-access2.md)  
  
 [SDLC Connection Parameters](../HIS2010/sdlc-connection-parameters1.md)  
  
 [X.25 Connection Parameters](../HIS2010/x-25-connection-parameters1.md)  
  
 [Sample VTAM Parameters](../HIS2010/sample-vtam-parameters2.md)  
  
 [Configuring VTAM for APPC Access](../HIS2010/configuring-vtam-for-appc-access2.md)  
  
 [Sample CICS Configuration Screens for Use with APPC](../HIS2010/sample-cics-configuration-screens-for-use-with-appc1.md)  
  
 [Configuring NCP for Independent APPC](../HIS2010/configuring-ncp-for-independent-appc2.md)  
  
 [Configuring the AS/400 for 5250 Access](../HIS2010/configuring-the-as-400-for-5250-access1.md)  
  
 [Table of Parameters for AS/400 Communication](../HIS2010/table-of-parameters-for-as-400-communication2.md)