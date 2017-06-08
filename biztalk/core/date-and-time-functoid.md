---
title: "Date and Time Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Date and Time functoids"
ms.assetid: dc2597f1-3031-4934-b42e-eac70df80994
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Date and Time Functoid
Use the **Date and Time** functoid ( ![](../core/media/datecurrentdatetime.gif "datecurrentdatetime")) to retrieve the current date and time in the format YYYY-MM-DDThh:mm:ss.  
  
## Input  
 None.  
  
## Output  
 **Output 1:** A date/time string in the format YYYY-MM-DDThh:mm:ss that represents the current date and time.  
  
## Remarks  
 The date and time formats used by this functoid are ISO 8601-compliant.  
  
 This functoid can be useful when a field in a destination message that is being created from a source message and a map is meant to contain a time stamp, such as the date and time when the message was processed.  
  
 The time portion of the output of this functoid is expressed by using a 24 hour notation (for example, 2 P.M. is expressed as "14:00:00").  
  
## See Also  
 [Date and Time Functoids Reference](../core/date-and-time-functoids-reference.md)   
 [Date and Time Functoids](../core/date-and-time-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)