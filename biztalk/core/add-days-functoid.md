---
title: "Add Days Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Add Days functoids"
ms.assetid: e59aaf65-864f-49ac-a8d4-b67ac4c00d3d
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Add Days Functoid
Use the **Add Days** functoid ( ![](../core/media/dateadddays.gif "dateadddays")) to add a specified number of days to a specified date.  
  
## Input  
 **Parameter 1:** A date string in the format YYYY-MM-DD or a date/time string in the format YYYY-MM-DDThh:mm:ss to which the specified number of days is added.  
  
 **Parameter 2:** A numeric value that is interpreted as the number of days to be added to the specified date.  
  
## Output  
 **Output 1:** A date string in the format YYYY-MM-DD that is the result of adding the specified number of days to the specified date.  
  
## Remarks  
 The date format used by this functoid is ISO 8601-compliant.  
  
 For example, suppose that your company always fulfills purchase orders within two days of receiving them. When you create a map that creates a purchase order acknowledgment from a purchase order, you can use the **Add Days** functoid to add two days to the current date (returned by the **Date** functoid) and use that value in the acknowledgment as the date by which the purchase order will be fulfilled.  
  
## See Also  
 [Date and Time Functoids Reference](../core/date-and-time-functoids-reference.md)   
 [Date and Time Functoids](../core/date-and-time-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)