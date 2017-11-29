---
title: "State Checks (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47c2fa02-5fa7-4365-b45c-3b0896bd80a7
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# State Checks (CPI-C)
A state check occurs when a transaction program (TP) issues a Common Programming Interface for Communications (CPI-C) call and the conversation is not in the appropriate state. For example, a state check occurs if a TP issues [Send_Data](../Topic/Send_Data%20\(CPI-C\)1.md) while the conversation is in RECEIVE state. When a state check occurs, CPI-C does not execute the call. It returns state check information through the *return_code* parameter.