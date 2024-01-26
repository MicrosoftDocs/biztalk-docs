---
description: "Learn more about: Already Verified Support"
title: "Already Verified Support"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Already Verified Support
In an implementation where a Host Integration Server application acts as a gateway between an SNA network and a non-SNA network, it is possible that non-Host Integration Server clients of the gateway may require Sync Point Level 2 conversation security. Since the originating client will have validated the relevant user identifier and password, the gateway application should specify conversation security of AP_SAME when starting a conversation on behalf of the client. In this case, however, Host Integration Server assumes that the user identifier to be used has previously been received on an Attach targeted at the TP. In the case of a non-Host Integration Server client this is not the case.  
  
 To allow such a gateway to support Sync Point Level 2 conversation security, Host Integration Server provides a new verb, [SET_TP_PROPERTIES](set-tp-properties2.md), which allows the gateway application to set the user identifier for the TP before allocating a conversation with security of AP_SAME. This verb will normally be issued once, immediately after [TP_STARTED](tp-started2.md), to set the user identifier for all the TP's conversations.
