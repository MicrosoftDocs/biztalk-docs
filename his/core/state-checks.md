---
title: "State Checks1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d205c478-e1b0-4dca-b6a0-427f8edeb470
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# State Checks
A state check occurs when a TP issues an APPC verb and the conversation is not in the appropriate state. For example, a state check occurs if a TP issues [MC_SEND_DATA](../Topic/MC_SEND_DATA2.md) while the conversation is in RECEIVE state. When a state check occurs, APPC does not execute the verb; it returns state check information through primary and secondary return codes.