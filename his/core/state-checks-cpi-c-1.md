---
description: "Learn more about: State Checks (CPI-C)"
title: "State Checks (CPI-C)1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# State Checks (CPI-C)
A state check occurs when a transaction program (TP) issues a Common Programming Interface for Communications (CPI-C) call and the conversation is not in the appropriate state. For example, a state check occurs if a TP issues [Send_Data](./send-data-cpi-c-2.md) while the conversation is in RECEIVE state. When a state check occurs, CPI-C does not execute the call. It returns state check information through the *return_code* parameter.
