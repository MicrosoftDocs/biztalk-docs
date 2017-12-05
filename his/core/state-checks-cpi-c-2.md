---
title: "State Checks (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 086f51dc-833d-4ce8-ba0c-16132e665ed5
caps.latest.revision: 3
---
# State Checks (CPI-C)
A state check occurs when a transaction program (TP) issues a Common Programming Interface for Communications (CPI-C) call and the conversation is not in the appropriate state. For example, a state check occurs if a TP issues [Send_Data](../core/send-data-cpi-c-1.md) while the conversation is in RECEIVE state. When a state check occurs, CPI-C does not execute the call. It returns state check information through the *return_code* parameter.