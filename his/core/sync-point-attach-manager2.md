---
title: "Sync Point Attach Manager2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af51cb71-f79e-42ad-85a0-ebed90c3e7c1
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Sync Point Attach Manager
Instead of issuing separate [RECEIVE_ALLOCATE](./receive-allocate1.md) verbs for each possible transaction name, a Sync Point implementation may instead register as the Sync Point Attach Manager for Host Integration Server. It does so by issuing a **RECEIVE_ALLOCATE** verb specifying a TP name consisting of all 0x00s.  
  
 When a Sync Point Attach Manager is registered, the following changes are effected in server's incoming Attach support on Host Integration Server:  
  
- When an Attach message arrives for any TP name on a conversation with the **syncpoint_rqd** field of the VCB set to AP_YES, Host Integration Server matches it with the application that issued the special **RECEIVE_ALLOCATE** verb registering itself as the Sync Point Attach Manager.  
  
- Any Attach message arriving for the Resynchronization TP (0x06F2) will automatically be routed to the Sync Point Attach Manager.  
  
- If no **RECEIVE_ALLOCATE** has been issued for the Sync Point Attach Manager, or for the specific TP name, Host Integration Server will queue the Attach for a configured period of time. If no **RECEIVE_ALLOCATE** is issued in that time, the Attach will be rejected with a return code of TP_NOT_AVAILABLE_RETRY.  
  
- If a **RECEIVE_ALLOCATE** is matched with the Attach message, the verb is returned to the TP with the **tp_name** field of the VCB set to the TP name contained in the Attach message.  
  
  Applications using this feature must adhere to two restrictions:  
  
- All verbs issued on conversations started in this manner must be issued by the same process, as Host Integration Server cannot pass **tp_id**s between processes.  
  
- Only a single process may register as the Sync Point Attach Manager on any server running Host Integration Server. If a second process attempts to register, its **RECEIVE_ALLOCATE** verb will return immediately with the primary return code set to AP_SYNCPOINT_MANAGER_ACTIVE.  
  
  Sync Point Attach Manager applications must reside on a Host Integration Server server. They may not be distributed across Host Integration Server clients. This restriction is imposed to ensure that only a single instance of Sync Point Services (SPS) and Conversation-Protected Resource Manager (C-PRM) exists for each LU on the Host Integration Server (which might not be the case if Sync Point Attach Managers were visible from multiple servers in the Host Integration Server domain).  
  
  The structure of the [RECEIVE_ALLOCATE](./receive-allocate1.md) verb control block does not require modification to support this function.