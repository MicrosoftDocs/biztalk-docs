---
title: "Support for APPC Automatic Logon2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ebf9e8c-bee3-4ed2-8de1-0a5a069d015c
caps.latest.revision: 3
---
# Support for APPC Automatic Logon
This section describes the support for automatic logon for Advanced Program-to-Program Communications (APPC) applications available in [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)]. This feature requires specific configuration by the network administrator.  
  
 The APPC application must be invoked on the local area network (LAN) side from a client of Host Integration Server. The client must be logged on to a Windows domain.  
  
 The client application is coded to use "program" level security, with a special hard-coded APPC user name (MS$SAME) and password (MS$SAME). When this session allocation flows from client to Host Integration Server, the server looks up the host account and password corresponding to the Windows account under which the client is logged on, and substitutes the host account information into the APPC attach message it sends to the host.  
  
 To use this feature for an APPC application, the **user_id** and **pwd** fields in the [ALLOCATE](../Topic/ALLOCATE1.md) or [MC_ALLOCATE](../Topic/MC_ALLOCATE1.md) verbs must be hard-coded to use the string mentioned above, and **security** must be set to AP_PGM.