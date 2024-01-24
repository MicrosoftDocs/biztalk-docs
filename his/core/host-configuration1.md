---
title: Host configuration
description: Learn more about host configuration.
ms.service: host-integration-server
ms.topic: conceptual
ms.date: 11/30/2017
---

# Host configuration

For a connection to be established successfully between a host computer and a [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer, a number of software configuration settings (VTAM, NCP, or IBM System i), and hardware characteristics must work together. These include the mainframe node ID settings, IBM System i name settings, addresses, BTU length, and link service settings.

## Important configuration items

Host configuration settings (VTAM, NCP, or IBM System i settings) must match the **Connection and Server** settings on [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].

- **Mainframe Node ID settings**

  For most mainframes, IDBLK and IDNUM in the PU definition must be matched by the two parts of the Remote Node ID on the Host Integration Server connection.

- **IBM System i name settings**

  For the IBM System i, local and remote Control Point Names (CP names) and network names must match corresponding Host Integration Server settings (local names configured on the server and remote names on the connection).

- **BTU length**

  For the mainframe, this is set through MAXDATA in the PU definition. For the IBM System i, this is set through MAXFRAME. These should equal the Max BTU Length on the Host Integration Server connection.

When you configure a new host connection or troubleshoot an existing connection, regardless of the connection type, the identifiers between the host and Host Integration Server must match. The following sections describe various configuration settings.

## In This Section

 [Mainframe Connections with XIDs](../core/mainframe-connections-with-xids1.md)  

 [Mainframe Connections without XIDs](../core/mainframe-connections-without-xids2.md)  

 [i Series Connections](../core/as-400-connections1.md)  

 [Configuring VTAM for 3270 Access](../core/configuring-vtam-for-3270-access1.md)  

 [Sample VTAM Parameters](../core/sample-vtam-parameters1.md)  

 [Configuring VTAM for APPC Access](../core/configuring-vtam-for-appc-access1.md)  

 [Sample CICS Configuration Screens for Use with APPC](../core/sample-cics-configuration-screens-for-use-with-appc2.md)  

 [Configuring NCP for Independent APPC](../core/configuring-ncp-for-independent-appc1.md)  

 [Configuring the IBM System i for 5250 Access](../core/configuring-the-as-400-for-5250-access2.md)  

 [Table of Parameters for IBM System i Communication](../core/table-of-parameters-for-as-400-communication1.md)
