---
description: "Learn more about: How the SQL Adapter Sample Works"
title: "How the SQL Adapter Sample Works | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77811152-cc8e-4090-89eb-e3a402a46e5e
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How the SQL Adapter Sample Works
The SQL Adapter sample provides a sample two-way itinerary configured with the routing service and a transform messaging service.  
  
 The routing service is configured with a STATIC resolver, which specifies that the message should be routed to execute a SQL stored procedure within the GlobalBankESB database named InsertProduct using the WCF-Custom adapter provider.  
  
 The transform service specifies a map that converts the incoming message to the format accepted by the InsertProduct stored procedure.
