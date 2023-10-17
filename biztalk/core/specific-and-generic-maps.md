---
description: "Learn more about: Specific and Generic Maps"
title: "Specific and Generic Maps"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Specific and Generic Maps
When you create a map that transforms data, you can create either a *specific* or a *generic* map.  
  
 You use a specific map to meet the needs of a particular trading partner. Use a specific map when you have very specific business needs or business agreements with your trading partner. The advantage of a specific map is that it is customized to meet the needs of the business functions you have with specific trading partners. The disadvantage of a specific map is that it cannot be used with multiple trading partners. If you multiply the number of trading partners by the number of different message types exchanged with those trading partners, you must allocate enough time and resources to manage all of the associated maps.  
  
 Generic maps, on the other hand, are designed to be used with multiple trading partners. Therefore, instead of developing and maintaining multiple schemas for a particular business document, you create one schema for each type of business document, and then use them with all of your trading partners. While using one map with multiple trading partners saves time and resources, these maps are not customized and may not be meet the needs of all cases.  
  
 It is likely that you will create both specific and generic maps, depending on the nature of your business.  
  
## See Also  
 [Maps](../core/maps.md)   
 [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md)
