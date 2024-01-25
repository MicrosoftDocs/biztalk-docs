---
description: "Learn more about: Choosing Modes"
title: "Choosing Modes1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Choosing Modes
When choosing modes, each LU-LU pair has a mode associated with it that determines session properties for that pair. For independent APPC LU sessions, the Parallel Session Limit parameter is of particular importance because this limit determines the number of simultaneous conversations that a session can support. If you plan to use a remote APPC LU that supports parallel sessions, it can only be used with a mode whose parallel session limit has a value greater than 1.  
  
 The following table lists the modes supplied with Host Integration Server and describes the scenarios in which each mode can be used.  
  
|Mode Name|Suitability|  
|---------------|-----------------|  
|#BATCH|Batch-oriented sessions|  
|#BATCHSC|Batch-oriented sessions that employ a minimal level of routing security|  
|BLANK|Sessions using a default node name, encoded as eight blank EBCDIC spaces in a BIND APPC command|  
|#INTER|Interactive sessions|  
|#INTERSC|Interactive sessions that employ a minimal level of routing security|  
|QPCSUPP|All sessions with an IBM i computer|  
  
## See Also  
 [APPC Deployment Strategies](../core/appc-deployment-strategies1.md)
