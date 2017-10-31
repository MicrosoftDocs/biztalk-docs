---
title: "Already Verified Support1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7225db20-f9f1-45c7-b104-a61da26d1976
caps.latest.revision: 3
---
# Already Verified Support
In an implementation where a Host Integration Server application acts as a gateway between an SNA network and a non-SNA network, it is possible that non-Host Integration Server clients of the gateway may require Sync Point Level 2 conversation security. Since the originating client will have validated the relevant user identifier and password, the gateway application should specify conversation security of AP_SAME when starting a conversation on behalf of the client. In this case, however, Host Integration Server assumes that the user identifier to be used has previously been received on an Attach targeted at the TP. In the case of a non-Host Integration Server client this is not the case.  
  
 To allow such a gateway to support Sync Point Level 2 conversation security, Host Integration Server provides a new verb, [SET_TP_PROPERTIES](../Topic/SET_TP_PROPERTIES1.md), which allows the gateway application to set the user identifier for the TP before allocating a conversation with security of AP_SAME. This verb will normally be issued once, immediately after [TP_STARTED](../Topic/TP_STARTED1.md), to set the user identifier for all the TP's conversations.