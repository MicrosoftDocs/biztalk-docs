---
title: "Defining RTM Thresholds1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b65f322d-869c-4a66-b7e8-1e53584342c8
caps.latest.revision: 3
---
# Defining RTM Thresholds
Response time monitor (RTM) data is collected by comparing host response times against a series of four boundary values. Each time a host transaction occurs, the response time is compared with the boundary values, and the appropriate counter is incremented. There is a counter for each of the four intervals defined by the boundary values, and an overflow counter for response times above the largest boundary value.  
  
 You can change the default boundaries — 0.5, 1, 2, and 5 seconds — using the SNA manager console. You also can select which of three response time definitions to set as default.  
  
 The response time is measured from the time the user presses ENTER until one of the following events occurs:  
  
-   The first character of host data reaches the 3270 display.  
  
-   The keyboard is unlocked.  
  
-   The user is enabled to send data.  
  
 A host can override the default boundaries and other host response time settings for any or all logical units (LUs) it controls.  
  
## See Also  
 [Specifying When RTM Data is Sent](../HIS2010/specifying-when-rtm-data-is-sent2.md)   
 [Indicating Lost RTM Data](../HIS2010/indicating-lost-rtm-data2.md)