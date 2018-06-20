---
title: "Sample Dehydration Calculation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4da41d0d-10ee-4f64-97d1-3cfa9da153f7
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sample Dehydration Calculation
Here is an example of a sample calculation, using private bytes, to determine if BizTalk will dehydrate or not. It uses the default configured values, and some example run-time values.  
  
 Assume the following values for the dehydration properties:  
  
- **TimeBlocked** = 60 (example time blocked in seconds)  
  
- **WaitingHistory** = 90 (example waiting history in seconds)  
  
- **ActualPrivateBytes** = 250 (example value for private bytes)  
  
- **OptimalUsage** = 50 (default configuration value)  
  
- **MaximalUsage** = 350 (default configuration value)  
  
  Since the **ActualPrivateBytes** are between **OptimalUsage** and **MaximalUsage**, alpha is calculated as:  
  
```  
alpha(private) = (350 – 250) / 350 – 50)  
alpha(private) = 100 / 300  
alpha(private) = 0.33  
```  
  
 Then you calculate the **TestThreshold** as follows:  
  
```  
TestThreshold = 1 + (0.33 * (1800 – 1))  
TestThreshold = 1 + 599.66  
TestThreshold = 600.66  
```  
  
 And finally, make the decision to dehydrate or not:  
  
```  
Dehydrate = (90 == -1 OR 90 > 600 OR 60 > (2 * 600))  
Dehydrate = false  
```  
  
 Using this example, you can determine that the orchestration will not be dehydrated at this time.