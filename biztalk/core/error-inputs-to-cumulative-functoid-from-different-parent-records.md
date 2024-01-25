---
description: "Learn more about: Error - Inputs to Cumulative Functoid from Different Parent Records"
title: "Error - Inputs to Cumulative Functoid from Different Parent Records"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.inputsToCumulativeFromDiffParents"
---
# Error - Inputs to Cumulative Functoid from Different Parent Records
**Error Code**  
  
 btm1032  
  
 **Explanation**  
  
 For the indicated **Cumulative** functoid, the second input parameter (the accumulation scope) is from a different part of the source schema than the node serving as the first input parameter (the node to accumulate).  
  
 **User Action**  
  
 Ensure that both input parameters to the indicated **Cumulative** functoid share the same parent record, or that the second input parameter (the accumulation scope) you provide has a constant input parameter.
