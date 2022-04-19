---
description: "Learn more about: Configuring Invokable TPs on Host Integration Server"
title: "Configuring Invokable TPs on Host Integration Server1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 736ec1f3-336b-4bb1-91ef-4d1add420332
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Configuring Invokable TPs on Host Integration Server
For a computer running Host Integration Server to receive allocation requests from an invoking TP on another system and route those requests to an invokable TP, certain parameters must be configured correctly:  
  
-   The Host Integration Server must have a connection to the system from which the invoking TP's request is sent.  
  
-   The Host Integration Server must have a remote LU capable of receiving the incoming request. This remote LU can be configured either explicitly or implicitly.  
  
     When configured explicitly, there is an explicit match between a remote LU alias on the Host Integration Server and the alias of the LU that conveys the invoking TP's request.  
  
     When configured implicitly, an implicit incoming remote LU (with its implicit incoming mode) is used. This means that several items must work together. First, the LU alias specified in the incoming request (the LU alias requested for the invokable TP) must match a local LU alias on the Host Integration Server receiving the request. Second, the local LU on the Host Integration Server server must have an implicit incoming remote LU assigned to it. The properties of the implicit incoming remote LU will be used for that LU-LU session. For more details about how an implicit incoming remote LU works, see Microsoft Host Integration Server Help.  
  
-   Appropriate local LUs must be defined in the Host Integration Server configuration. For descriptions of several ways to set up these local LUs, see [Arranging TPs Within an SNA Network](../core/arranging-tps-within-an-sna-network2.md).
