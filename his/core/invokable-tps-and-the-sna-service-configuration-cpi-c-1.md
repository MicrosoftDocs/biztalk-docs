---
title: "Invokable TPs and the SNA Service Configuration (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dd01f458-b0f7-4e77-9617-a6d22b3b5a57
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Invokable TPs and the SNA Service Configuration (CPI-C)
For an SNA service to receive allocation requests from an invoking transaction program (TP) on another system and route those requests to an invokable TP, certain parameters must be configured correctly:  
  
-   The SNA service must have a connection to the system from which the invoking TP's request is sent.  
  
-   The SNA service must have a remote logical unit (LU) capable of receiving the incoming request. This remote LU can be configured either explicitly or implicitly.  
  
     When configured explicitly, there is an explicit match between a remote LU alias on the SNA service and the alias of the LU that conveys the invoking TP's request.  
  
     When configured implicitly, an implicit incoming remote LU (with its implicit incoming mode) is used. This means that several items must work together. First, the LU alias specified in the incoming request (the LU alias requested for the invokable TP) must match a local LU alias on the SNA service receiving the request. Second, the local LU on the server must have an implicit incoming remote LU assigned to it. The properties of the implicit incoming remote LU will be used for that LU-LU session.  
  
-   Appropriate local LUs must be defined in the SNA service configuration. For descriptions of several ways to set up these local LUs, see [Arranging TPs Within an SNA Network](../core/arranging-tps-within-an-sna-network-cpi-c-2.md).