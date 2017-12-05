---
title: "Subcategories for Invokable TPs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d596df4c-0252-423d-a845-bd5bf17d8033
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Subcategories for Invokable TPs
The following figure shows subcategories for invokable TPs.  
  
|Queued<br /><br /> or nonqueued|Application<br /><br /> or service|Starting method|  
|-----------------------------|--------------------------------|---------------------|  
|Queued|Running as an application or a service|Autostarted or operator-started|  
|Nonqueued|Running as an application|Autostarted|  
  
 The concept of a TP "running as a service" or "running as an application" is distinct from a service TP or an application TP. Service TP and application TP are SNA terms that describe how a TP is used: either as a supportive service program for other APPC programs, or directly by a user, as an application. For detailed information about services and applications on Windows, see the Microsoft Developer Network (MSDN®) Platform Software Development Kit.  
  
 To write an autostarted TP so it will run under Windows as a service and also run in a nonqueued way, write a multithreaded program with a [RECEIVE_ALLOCATE](../core/receive-allocate2.md) always outstanding. See [Invokable TPs](../core/invokable-tps2.md).