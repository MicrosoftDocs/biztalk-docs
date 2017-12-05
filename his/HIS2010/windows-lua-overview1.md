---
title: "Windows LUA Overview1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d88e59c5-0808-4ffb-9e9e-d5c8d209adb7
caps.latest.revision: 5
---
# Windows LUA Overview
To provide one common application programming interface (API) to port applications from various operating environments to Windows operating systems, a Windows Systems Network Architecture (SNA) standard was created. As a direct result of this work, Windows logical unit application (LUA) was developed. The LUA verbs, routines, and information presented in this guide represent an evolving Windows LUA that is based on IBM Extended Services for OS/2 version 1.0 and includes a set of Windows extensions.  
  
 The use of the Windows LUA interface on Windows operating system causes additional threads to be created within the calling process. These other threads perform interprocess communication with the SNA service over the LAN interface that the client is configured to use (for example, TCP/IP or named pipes).  
  
 If an application using LUA is running Windows operating systems, stopping the SNABASE service causes the application to be unloaded from memory.  
  
 This section contains:  
  
-   [Windows LUA Asynchronous Support](../HIS2010/windows-lua-asynchronous-support2.md)  
  
-   [Before Using Windows LUA](../HIS2010/windows-lua-considerations1.md)  
  
-   [Using LUA and Asynchronous Verb Completion](../HIS2010/lua-and-asynchronous-verb-completion1.md)