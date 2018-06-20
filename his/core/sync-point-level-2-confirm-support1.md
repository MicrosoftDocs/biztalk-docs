---
title: "Sync Point Level 2 Confirm Support1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b81e05ca-5e55-475b-933b-b98a4f96f7b1
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Sync Point Level 2 Confirm Support
The current APPC implementation in Host Integration Server supports conversations with **synclevel** of AP_NONE, AP_CONFIRM_SYNC_LEVEL, or AP_SYNCPT. The [DEALLOCATE](./deallocate2.md), [MC_DEALLOCATE](./mc-deallocate2.md), [PREPARE_TO_RECEIVE](./prepare-to-receive2.md), and [MC_PREPARE_TO_RECEIVE](./mc-prepare-to-receive1.md) verbs specify a **type** member indicating the synchronization level required. This parameter is interpreted as follows:  
  
|Allocated synclevel|Type specified|Action performed|  
|-------------------------|--------------------|----------------------|  
|AP_NONE|AP_FLUSH|Action of [FLUSH](./flush2.md) or [MC_FLUSH](./mc-flush1.md) verb before deallocation or change of direction.|  
|AP_NONE|AP_SYNCLEVEL|Action of **FLUSH** or **MC_FLUSH** verb before deallocation or change of direction.|  
|AP_SYNCPT|AP_FLUSH|Action of [FLUSH](./flush2.md) or [MC_FLUSH](./mc-flush1.md) verb before deallocation or change of direction.|  
|AP_SYNCPT or  AP_CONFIRM_SYNC_LEVEL|AP_CONFIRM_TYPE|Action of [CONFIRM](./confirm2.md) or [MC_CONFIRM](./mc-confirm2.md) verb before deallocation or change of direction.|  
|AP_SYNCPT|AP_SYNCLEVEL|It is assumed that a Sync Point implementation built using the APPC API in Host Integration Server implements the defer states appropriately. See the note below.|  
  
> [!NOTE]
>  With an allocated **synclevel** of AP_SYNCPT and a specified **type** of AP_SYNCLEVEL, it is assumed that a vendor-supplied Sync Point component implements the defer states appropriately. A vendor-supplied Sync Point system must:  
  
- Intercept [DEALLOCATE](./deallocate2.md), [MC_DEALLOCATE](./mc-deallocate2.md), [PREPARE_TO_RECEIVE](./prepare-to-receive2.md), and [MC_PREPARE_TO_RECEIVE](./mc-prepare-to-receive1.md) verbs on Sync Point Level 2 conversations when type AP_SYNCLEVEL is specified for **synclevel**.  
  
- Maintain the defer state until one of the verbs valid in that state completes.  
  
- On completion of the verb, issue the original **DEALLOCATE**, **MC_DEALLOCATE**, **PREPARE_TO_RECEIVE**, or **MC_PREPARE_TO_RECEIVE** verb to Host Integration Server.  
  
  Host Integration Server does not implement the defer states directly. In particular, when a **DEALLOCATE**, **MC_DEALLOCATE**, **PREPARE_TO_RECEIVE**, or **MC_PREPARE_TO_RECEIVE** verb is received with a **type** specified as AP_SYNCLEVEL on a Sync Point conversation, this is treated as if the conversation has a **synclevel** of AP_NONE.  
  
  So that Sync Point Level 2 conversations can use confirm type synchronization, the **DEALLOCATE**, **MC_DEALLOCATE**, **PREPARE_TO_RECEIVE**, and **MC_PREPARE_TO_RECEIVE** verbs are modified to support a type member of AP_CONFIRM_TYPE.  
  
  The [DEALLOCATE](./deallocate2.md), [MC_DEALLOCATE](./mc-deallocate2.md), [PREPARE_TO_RECEIVE](./prepare-to-receive2.md), and [MC_PREPARE_TO_RECEIVE](./mc-prepare-to-receive1.md) verbs specify a type member indicating the synchronization level required. This parameter is interpreted as follows:  
  
|Allocated synclevel|Type specified|Action performed|  
|-------------------------|--------------------|----------------------|  
|AP_NONE|AP_FLUSH|Action of [FLUSH](./flush2.md) or [MC_FLUSH](./mc-flush1.md) verb before deallocation or change of direction.|  
|AP_NONE|AP_SYNCLEVEL|Action of **FLUSH** or **MC_FLUSH** verb before deallocation or change of direction.|  
|AP_CONFIRM_SYNC_LEVEL|AP_FLUSH|Action of **FLUSH** or **MC_FLUSH** verb before deallocation or change of direction.|  
|AP_CONFIRM_SYNC_LEVEL|AP_SYNCLEVEL|Action of [CONFIRM](./confirm2.md) or [MC_CONFIRM](./mc-confirm2.md) verb before deallocation or change of direction.|