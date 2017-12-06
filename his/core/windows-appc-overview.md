---
title: "Windows APPC Overview2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2562e864-c675-40df-9d3e-b85e37739941
caps.latest.revision: 5
author: MandiOhlinger
manager: anneta
---
# Windows APPC Overview
The information provided in this guide is source code and executable code compatible with the following implementations of APPC:  
  
-   APPC applications based on [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] residing on the server or on a client. These applications run on Microsoft operating systems.  
  
 Programs written to use this implementation of APPC can exchange data with programs written to use other implementations of APPC that adhere to the SNA LU 6.2 architecture.  
  
 The use of the APPC interface on Windows operating systems causes additional threads to be created within the calling process. These other threads perform interprocess communication with the Host Integration Server or SNA service over the LAN interface that the client is configured to use (TCP/IP or named pipes, for example).  
  
 If an application using APPC is running on Windows operating systems, stopping the SNABASE service causes the application to be unloaded from memory.  
  
## In This Section  
 [Windows APPC Asynchronous Support](../core/windows-appc-asynchronous-support.md)  
  
 [APPC Verbs and Windows Extensions](../core/appc-verbs-and-windows-extensions.md)