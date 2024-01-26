---
description: "Learn more about: Allocation Failure"
title: "Allocation Failure1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Allocation Failure
If you used one of the modes that come pre-packaged with [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)], that mode can attempt to dynamically create a session with the partner. This fails with an abnormal CNOS reply, "mode name not recognized." The error returned by the APPC API is ALLOCATION FAILURE - RETRY. This leads to an error stating: "The TI LU 6.2 transport failed to allocate conversation, make sure that host LU (hostname) is active, and retry the operation."  
  
 You will see this same error when you try to create a session with a CICS region that is not active.  
  
 To avoid this problem, upon entering SNA Manager in [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)], add the LUs and modes that you will be using and delete any pre-supplied modes that you will not be using.
