---
description: "Learn more about: Windows APPC Overview"
title: "Windows APPC Overview2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Windows APPC Overview
The information provided in this guide is source code and executable code compatible with the following implementations of APPC:  
  
- APPC applications based on Host Integration Server residing on the server or on a client. These applications run on Microsoft operating systems.  
  
  Programs written to use this implementation of APPC can exchange data with programs written to use other implementations of APPC that adhere to the SNA LU 6.2 architecture.  
  
  The use of the APPC interface on Windows operating systems causes additional threads to be created within the calling process. These other threads perform interprocess communication with the Host Integration Server or SNA service over the LAN interface that the client is configured to use (TCP/IP or named pipes, for example).  
  
  If an application using APPC is running on Windows operating systems, stopping the SNABASE service causes the application to be unloaded from memory.  
  
## In This Section  
 [Windows APPC Asynchronous Support](../core/windows-appc-asynchronous-support2.md)  
  
 [APPC Verbs and Windows Extensions](../core/appc-verbs-and-windows-extensions1.md)
