---
title: "How to Calculate Dehydration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88f2d09c-60db-4daf-b850-23f2c8915502
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Calculate Dehydration
To calculate dehydration, you use the configured properties and certain run-time values. The following example demonstrates how to calculate a hypothetical dehydration scenario.  
  
### To calculate dehydration  
  
1. Let alpha represent a factor between 0 and 1 that measures memory stress.  In practice, alpha has a component for each of the three memory throttling criteria (dehydration properties); in this example we denote them as alpha(virtual), alpha(private) and alpha(physical). Define the following:  
  
   ```  
   IF ActualPrivateBytes < OptimalUsage  
      alpha(private) = 1  
   ELSE IF ActualPrivateBytes > MaximalUsage  
      alpha(private) = 0  
   ELSE  
      alpha(private) = (MaximalUsage - ActualPrivateBytes) / (MaximalUsage - OptimalUsage)  
   ```  
  
   > [!NOTE]
   >  OptimalUsage and MaximalUsage have default values for each dehydration property. These values can be changed in the BTSNTSvc.exe.config file. For more information, see [Dehydration Default Properties](../core/dehydration-default-properties.md).  
  
2. Define the other alpha components analogously. Define the following:  
  
   ```  
   alpha = Minimum { alpha(virtual), alpha(private), alpha(physical) }  
   where alpha(…) = 1 whenever IsActive=false for that given memory unit  
   ```  
  
3. Then define TestThreshold (TestThreshold, MinThreshold, and MaxThreshold are defined in seconds):  
  
   ```  
   TestThreshold = MinThreshold + (alpha * (MaxThreshold – MinThreshold))  
   ```  
  
   > [!NOTE]
   >  MinThreshold default value = 1. MaxThreshold default value = 1800. These values can be changed in the BTSNTSvc.exe.config file. For more information, see [Dehydration Default Properties](../core/dehydration-default-properties.md).  
  
4. Then define TimeBlocked and EstimatedTime:  
  
   -   TimeBlocked = actual time we have been waiting for this subscription to be satisfied  
  
   -   EstimatedTime = estimated time that this orchestration will remain idle (e.g. remaining timeout on the listen)  
  
   The decision whether to dehydrate is the result of the following Boolean condition (true = dehydrate):  
  
-   Dehydrate = (EstimatedTime > TestThreshold OR TimeBlocked > (2* TestThreshold))  
  
> [!NOTE]
>  Estimated time is the time remaining until the delay is ended (if delayed for 5 minutes and 2 minutes has passed, TimeBlocked=120 seconds, EstimatedTime=180 seconds).  
  
## See Also  
 [Dehydration Default Properties](../core/dehydration-default-properties.md)   
 [BTSNTSvc.exe.config File](../core/btsntsvc-exe-config-file.md)