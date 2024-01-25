---
description: "Learn more about: Locally Initiated Conversations"
title: "Locally Initiated Conversations1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Locally Initiated Conversations
Conversations are initiated locally by issuing an [ALLOCATE](./allocate2.md) or [MC_ALLOCATE](./mc-allocate2.md) verb. The **ALLOCATE** and **MC_ALLOCATE** verbs are modified to support additional parameters required by Sync Point support. The supplied **synclevel** parameter of the **ALLOCATE** and **MC_ALLOCATE** verbs can take on a value of AP_SYNCPT, which specifies that the conversation requested is a Sync Point conversation.
