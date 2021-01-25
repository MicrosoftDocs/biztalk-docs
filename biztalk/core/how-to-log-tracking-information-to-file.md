---
description: "Learn more about: How to Log Tracking Information to File"
title: "How to Log Tracking Information to File | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Business Rules Framework, tracking"
  - "DebugTrackingInterceptor"
  - "Business Rules Framework, code samples"
ms.assetid: c832b763-aa08-4a0e-9086-776dccb0a6ef
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Log Tracking Information to File
When the Business Rule Engine executes, it passes execution tracking information to an interceptor. The engine is configured to use the BizTalk interceptor which is used when tracking message events and service instance data. If you are calling the engine outside of BizTalk orchestration, you can pass the interceptor you want to use when you execute the policy. In addition to the BizTalk interceptor, you can also use the **DebugTrackingInterceptor** to output the tracking information to file. The following code example demonstrates how to use **DebugTrackingInterceptor**.  
  
```  
DebugTrackingInterceptor tracker = new DebugTrackingInterceptor("TrackingOutput.txt");  
policy.Execute(shortTermFacts,tracker);  
```
