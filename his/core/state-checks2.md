---
title: "State Checks2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 89265790-95c6-4eb7-abb0-660a0511bb21
caps.latest.revision: 3
---
# State Checks
A state check occurs when a TP issues an APPC verb and the conversation is not in the appropriate state. For example, a state check occurs if a TP issues [MC_SEND_DATA](../core/mc-send-data2.md) while the conversation is in RECEIVE state. When a state check occurs, APPC does not execute the verb; it returns state check information through primary and secondary return codes.