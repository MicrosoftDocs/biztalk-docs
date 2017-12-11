---
title: "Support for APPC Automatic Logon1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b21475d8-38f7-42a5-b3c4-497d930cd704
caps.latest.revision: 5
---
# Support for APPC Automatic Logon
This section describes the support for automatic logon for Advanced Program-to-Program Communications (APPC) applications available in [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]. This feature requires specific configuration by the network administrator.  
  
 The APPC application must be invoked on the local area network (LAN) side from a client of Host Integration Server. The client must be logged on to a Windows domain.  
  
 The client application is coded to use "program" level security, with a special hard-coded APPC user name (MS$SAME) and password (MS$SAME). When this session allocation flows from client to Host Integration Server, the server looks up the host account and password corresponding to the Windows account under which the client is logged on, and substitutes the host account information into the APPC attach message it sends to the host.  
  
 To use this feature for an APPC application, the **user_id** and **pwd** fields in the [ALLOCATE](../HIS2010/allocate1.md) or [MC_ALLOCATE](../HIS2010/mc-allocate1.md) verbs must be hard-coded to use the string mentioned above, and **security** must be set to AP_PGM.