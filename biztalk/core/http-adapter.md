---
description: "Learn more about: HTTP Adapter"
title: "HTTP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HTTP adapters, receive adapters"
  - "HTTP adapters, send adapters"
  - "HTTP adapters"
  - "receive adapters, HTTP adapters"
  - "send adapters, HTTP adapters"
  - "HTTP adapters, about HTTP adapters"
ms.assetid: a9423052-8392-4006-ab46-79834169c796
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTP Adapter
You use the HTTP adapter to exchange information between Microsoft BizTalk Server and an application by means of the HTTP protocol. HTTP is the primary protocol for interbusiness message exchange. Applications can send messages to a server by sending HTTP POST or HTTP GET requests to a specified HTTP URL. The HTTP adapter receives the HTTP requests and submits them to BizTalk Server for processing. Similarly, BizTalk Server can transmit messages to remote applications by sending HTTP POST requests to a specified HTTP URL.  
  
 The HTTP adapter consists of two adapters—a receive adapter and a send adapter. The HTTP receive adapter is a Microsoft Internet Information Services (IIS) Internet Server Application Programming Interface (ISAPI) extension that the IIS process hosts, and controls the receive locations that use the HTTP adapter. The HTTP send adapter controls the send ports that use the HTTP adapter.  
  
 This section discusses the workflow and batching support for both the HTTP receive adapter and the HTTP send adapter.  
  
## In This Section  
  
-   [HTTP Receive Adapter](../core/http-receive-adapter.md)  
  
-   [HTTP Send Adapter](../core/http-send-adapter.md)  
  
-   [Configuring the HTTP Adapter](../core/configuring-the-http-adapter.md)  
  
-   [HTTP Adapter Security Recommendations](../core/http-adapter-security-recommendations.md)
