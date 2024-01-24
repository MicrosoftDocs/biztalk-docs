---
description: "Learn more about: Date and Time Functoids"
title: "Date and Time Functoids"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Date and Time Functoids

## Overview
**Date / Time** functoids can be divided into two categories. The first category contains a single functoid, **Add Days**, which is used to add a specified number of days to a specified date and time value. This can be useful when a field in the output instance message is supposed to include a date and time estimate in the future. For example, the **Add Days** functoid can be used to generate an estimated shipping date based a fixed delta from the date that an order was received.  

 The second category includes all of the remaining functoids in the **Date and Time** category. They are used to provide a timestamp at run time, so that the date and time at which message transformation is being performed can be included in the output instance message.  

 The **Add Days** functoid accepts two input parameters, whereas the **Date**, **Date and Time**, and **Time** functoids have no input parameters.  

## Available functoids  
 The **Date / Time** functoids are: 

* Add Days
* Date
* Date and Time
* Time

More details on these functoids are available **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

## See Also  
- [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)   
- **Date and Time Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
