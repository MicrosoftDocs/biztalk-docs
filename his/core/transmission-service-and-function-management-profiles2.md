---
title: "Transmission Service and Function Management Profiles2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 230470e5-79ee-4d98-82f4-d13e2dfbf6c6
caps.latest.revision: 4
---
# Transmission Service and Function Management Profiles
[!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] enforces the rules that govern active sessions between communicating partners on an SNA network.  
  
 The Host Integration Server computer can select some of these session protocols—such as request/response control modes, bracket usage, and pacing—when you activate a session. The term "profiles" refers to specific combinations of these selectable protocol options.  
  
 Transmission service (TS) profiles refer to transmission control options, while function management (FM) profiles refer to data flow control and function management data options.  
  
 When activated, TS and FM profiles of a session are specified by using parameters in the appropriate session activation request and response such as ACTPU, ACTLU, BIND.  
  
 The following table specifies the TS and FM profiles supported by each of the Host Integration Server session types.  
  
|Session type|TS profiles|FM profiles|  
|------------------|-----------------|-----------------|  
|SSCP-LU session|1|0|  
|SSCP-PU session|1|0|  
|3270 display and printer PLU-SLU session|3|3|  
|LU 6.2 PLU-SLU session|7|19|  
|LUA PLU-SLU session|2, 3, 4|2, 3, 4, 7, 18|  
  
## In This Section  
 [TS Profile 1](../core/ts-profile-11.md)  
  
 [TS Profile 2](../core/ts-profile-21.md)  
  
 [TS Profile 3](../core/ts-profile-32.md)  
  
 [TS Profile 4](../core/ts-profile-41.md)  
  
 [TS Profile 7](../core/ts-profile-71.md)  
  
 [FM Profile 0](../core/fm-profile-01.md)  
  
 [FM Profile 2](../core/fm-profile-22.md)  
  
 [FM Profile 3](../core/fm-profile-32.md)  
  
 [FM Profile 4](../core/fm-profile-41.md)  
  
 [FM Profile 7](../core/fm-profile-71.md)  
  
 [FM Profile 18](../core/fm-profile-181.md)  
  
 [FM Profile 19](../core/fm-profile-191.md)