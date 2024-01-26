---
description: "Learn more about: FM Profile 2"
title: "FM Profile 21"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# FM Profile 2
Function management (FM) Profile 2 is supported on primary logic unit-secondary logic unit (PLU-SLU) sessions using LU 0. This profile uses the following session rules:  
  
- SLU uses delayed request mode.  
  
- SLU uses immediate response mode.  
  
- Only single-RU chains are allowed.  
  
- SLU requests indicate no-response.  
  
- No FMH-1 SCB compression.  
  
- Length-checked compression allowed.  
  
- No data flow control (DFC) RUs.  
  
- No FM headers.  
  
- SLU is the first speaker if brackets are used.  
  
- Bracket termination rule 2 is used if brackets are used.  
  
- PLU will send an end bracket (EB).  
  
- SLU will not send an EB.  
  
- Normal-flow send/receive mode is full duplex (FDX).  
  
- PLU is responsible for recovery.  
  
  The following FM Usage fields define the options for Profile 2:  
  
- Primary request control mode selection  
  
- Primary chain response protocol (no-response cannot be used)  
  
- Brackets usage and reset state  
  
- Alternate code  
  
## See Also  
 [Transmission Service and Function Management Profiles](../core/transmission-service-and-function-management-profiles1.md)
