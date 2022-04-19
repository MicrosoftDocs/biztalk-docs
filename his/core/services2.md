---
description: "Learn more about: Services"
title: "Services | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 188d7c7f-7862-413a-9c69-60635e941171
caps.latest.revision: 2
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Services
Under the Services Node the definitions for how to handle incoming traffic are created. There are seven different service types that are processed by the HIP runtime.

1. **ELM Link** - Incoming TCP/IP Call
2. **ELM User Data** - Incoming TCP/IP Call
3. **HTTP** - Incoming http call
4. **SNA Link** - Incoming APPC Link to program call from CICS on a mainframe
5. **SNA Endpoint** - Incoming APPC program call from a mainframe
6. **SNA User Data** - Incoming APPC program call from a mainframe
7. **TRM Link** - Incoming TCP/IP call

Each of the service types have parameters available to identify incoming requests and how to process those requests.

All service types include the following:

* **Service Name** - default is (service type name)1
* **Assembly Path** - the location where the implementing and metadata assemblies are kept 
* **Hosts** - the host environment(s) for allowed incoming calls - as defined under TCP Host Environments or SNA Host Environments

Other parameters are available depending upon the service type:

* **Request Header Format** - for TCP service types, default is Microsoft
* **Ports** - the port number(s) to listen on for incoming TCP/IP calls, separated by semi colons
* **Local LU Name** - for incoming APPC calls, the Local LU Name as defined in the SNA Manager

When the service type is configured, there is a node available named Resolution Entries. This is where the configuration is done to determine from the incoming data what customer HIP Method will be called. Right-click Resolution Entries and the Add Host-Initiated Processing Resolution Entry window will appear. The methods available in assemblies located in the Assembly Path of the service can be selected.  For each of the service types there are various Resolution Criteria options that are available.

