---
description: "Learn more about: Remote Environments"
title: "WIPRemoteEnvs | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b092a8c7-a5a7-4e98-8d96-2b725d68f1ca
caps.latest.revision: 6
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Remote Environments

There are 14 different Remote Environment types that can be configured. A remote environment defines the characteristics of the non-Windows host environment that receives requests from Windows-initiated processing (WIP) components. The Remote Environment that is defined must match the Remote Environment type the for the TI Meta data object.

## Environments list

Right-click the Remote Environments node and select New to bring up the list of the Remote Environments to choose from.  See the Related Sections below to explore which is the appropriate programming model for various environments.

1. **Distributed Program Call** - TCP/IP call to an iSeries system via DPC
2. **ELM Link** - TCP/IP call to a link to program in CICS on a mainframe
3. **ELM User Data** - TCP/IP call to a transaction in CICS on a mainframe
4. **HTTP Link** - http call to a link to program in CICS on a mainframe
5. **HTTP User Data** - http call to a transaction in CICS on a mainframe
6. **IMS Connect** - TCP/IP call to a program in IMS on a mainframe
7. **IMS LU62** - APPC call via the HIS Gateway to a program in IMS on a mainframe
8. **SNA Link** - APPC call via the HIS Gateway to a link to program in CICS on a mainframe
9. **SNA User Data** - APPC call via the HIS Gateway to a transaction in CICS on a mainframe
10. **System I Sockets User Data** - TCP/IP call to a program on an iSeries system
11. **System Z Sockets Link** - TCP/IP call to a program on the mainframe
12. **System Z Sockets User Data** - TCP/IP call to a program on the mainframe
13. **TRM Link** - TCP/IP call to a link to program in CICS on a mainframe
14. **TRM User Data** - TCP/IP call to a transaction in CICS on a mainframe

For each Remote Environment type there are a number of parameters available to identify the endpoint where the data will be sent and information about how the WIP Runtime will handle the call.

All Remote Environments include the following:

* **Name** - default is (Remote Environment Type Name) RE 1
* **Is Default** - default is false
* **Timeout** - default is 10 (seconds)
* **Code Page** - default is 37

Other parameters are available depending upon the programming model:

* **ESSO Affiliate Application** - default is null
* **Security from Client Context** - default is False
* **Certificate Common Name** - if using SSL, default is null
* **Server Verification Required** - if using SSL, default is False
* **Use SSL** - default is False
* **IP Address** - the IP address or DNS name of the backend host system
* **Ports** - the port number(s) separated by semicolons
* **TCP CICS Request Header Format** - used by TRM and ELM - default is Microsoft
* **Alias Transaction Id** - used by http - default is MSTX
* **Allow Redirects** - used by http - default is False
* **User Agent** - used by http - default is null
* **Mirror Program** - used by http link - default is MSHMIRS
* **IMS Inbound Header Format** - used by IMS Connect - default is HWSIMSO0
* **IMS System Id** - used by IMS Connect - default is IMSID1
* **ITOC Exit Name** - used by IMS Connect - default is *IRMREQ*
* **Mfs Mode Name** - used by IMS Connect - default is DFSMO1
* **Local LU Name** - used by APPC - default is null
* **Remote LU Name** - used by APPC - default is null
* **Mode Name** - used by APPC - default is null
* **Sync Level 2 Supported** - used by APPC - default is False
* **Allow Explicit Sync Point** - used by APPC to CICS - default is False
* **Mirror Transaction Id** - used by APPC to CICS Link - default is null
* **Override SNA Source Transaction Program** - used by APPC to CICS Link - default is False

## Related Sections

[Choosing the Appropriate Programming Model](../core/choosing-the-appropriate-programming-model1.md)
