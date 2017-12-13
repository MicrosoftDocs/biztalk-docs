---
title: "APPC Mode2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a8e9c31-45bd-46dc-af05-3ffec77e6c57
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# APPC Mode
A mode is associated with an LU-LU pair, and determines the session properties for that pair. One of the key mode properties is the Parallel Session Limit. This limit determines whether an LU-LU pair can perform only one interaction at a time or multiple concurrent interactions.  
  
 Parallel sessions are used only with independent APPC. If parallel sessions are to be allowed with an LU-LU pair, the local LU must be independent, and the remote LU in the pair must support parallel sessions.  
  
 If the LU-LU pair can have multiple parallel sessions, other mode properties, such as Minimum Contention-Winner Limit, determine to what extent each LU can initiate interactions.  
  
 The following table lists the modes provided with Host Integration Server.  
  
|Mode name|To be used for|  
|---------------|--------------------|  
|#BATCH|Batch-oriented sessions|  
|#BATCHC|Batch-oriented sessions using compression|  
|#BATCHSC|Batch-oriented sessions that employ a minimal level of routing security|  
|BLANK|Sessions using a default mode name, encoded as eight blank EBCDIC spaces in BIND|  
|#INTER|Interactive sessions|  
|#INTERC|Interactive sessions using compression|  
|#INTERSC|Interactive sessions that employ a minimal level of routing security|  
|QPCSUPP|All sessions with an AS/400 computer|  
||  
  
## See Also  
 [APPC Mode Definition](../core/appc-mode-definition2.md)   
 [Understanding Connectivity](../core/understanding-connectivity1.md)