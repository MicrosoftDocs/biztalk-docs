---
description: "Learn more about: Sync Point Session Deactivation"
title: "Sync Point Session Deactivation1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Sync Point Session Deactivation
A Sync Point implementation needs to determine whether it has lost connectivity to a partner when establishing Sync Point conversations so that it can know whether or not to resynchronize. To obtain this information, Host Integration Server provides a new APPC verb, [GET_LU_STATUS](./get-lu-status2.md) that reports the status of a particular remote LU. The information returned by this verb is as follows:  
  
- Current number of active LU 6.2 sessions between the remote LU and the TP's local LU.  
  
- Whether or not the number of active sessions dropped to zero at any time since this verb was last issued for the remote LU.  
  
  Note that the zero sessions indicator is reset to AP_NO each time the verb is issued by any process. It is therefore imperative that only one process issues this verb; otherwise information may be lost.
