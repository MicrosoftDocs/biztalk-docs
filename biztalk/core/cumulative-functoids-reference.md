---
title: "Cumulative Functoids Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cumulative functoids"
  - "Cumulative functoids, properties"
  - "functoid types, Cumulative"
ms.assetid: ee3b72df-92f3-4516-973a-c439eae1c150
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Cumulative Functoids Reference
Use **Cumulative** functoids to perform various types of accumulation operations for values that occur multiple times within an instance message. For example, you can use the **Cumulative Sum** functoid to provide the combined total for a value that occurs in multiple records within a specified scope in an instance message.  
  
 In Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], all **Cumulative** functoids accept two input parameters, the second of which is an optional scoping parameter that was not used in the **Cumulative** functoids in earlier versions of BizTalk Server. The two parameters are:  
  
-   **Parameter 1:** The value to be accumulated. This value must be numeric for all **Cumulative** functoids other than the **Cumulative Concatenate** functoid, which expects a string value. You supply this value by creating a link between a **Field Attribute**, **Field Element**, or **Record** (with its **Mixed** property set to **True**) node that has an appropriate data type and the **Cumulative** functoid.  
  
    > [!NOTE]
    >  If none of the ancestor **Record** nodes in the schema tree are repeating, using a **Cumulative** functoid is pointless.  
  
-   **Parameter 2:** The scope to which the value specified as the first parameter should be accumulated. This optional numeric value indicates how closely "related" the specified values in an instance message must be in order to participate in the accumulation, as follows:  
  
    -   The default value of zero (0) indicates that the element or attribute value, as indicated by its element or attribute name, should be accumulated over the entire instance message.  
  
    -   A scoping value of one (1) indicates that only element or attribute values that have the same parent element should be accumulated.  
  
    -   A scoping value of two (2) indicates that only element or attribute values that have the same grandparent element should be accumulated, and so on.  
  
> [!NOTE]
>  All **Cumulative** functoids provide backward compatibility with Microsoft [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] and Microsoft [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)], both of which required only one input parameter. They default to a scoping parameter of zero (0), meaning a scope of the entire instance message.  
  
 For additional conceptual information about **Cumulative** functoids, including the scoping parameter, see [Cumulative Functoids](../core/cumulative-functoids.md).  
  
 The following table shows the functoids in the **Cumulative** category.  
  
|Cumulative functoid|Description|  
|-------------------------|-----------------|  
|![](../core/media/cumulativeavg.gif "cumulativeavg") [Cumulative Average](../core/cumulative-average-functoid.md)|Calculates the accumulated average of a numeric value that recurs within corresponding instance messages.|  
|![](../core/media/cumulativeconcat.gif "cumulativeconcat") [Cumulative Concatenate](../core/cumulative-concatenate-functoid.md)|Concatenates multiple instances of a string value that recurs within corresponding instance messages.|  
|![](../core/media/cumulativemax.gif "cumulativemax") [Cumulative Maximum](../core/cumulative-maximum-functoid.md)|Determines the maximum value of a numeric value that recurs within corresponding instance messages.|  
|![](../core/media/cumulativemin.gif "cumulativemin") [Cumulative Minimum](../core/cumulative-minimum-functoid.md)|Determines the minimum value of a numeric value that recurs within corresponding instance messages.|  
|![](../core/media/cumulativesum.gif "cumulativesum") [Cumulative Sum](../core/cumulative-sum-functoid.md)|Calculates the accumulated sum of a numeric value that recurs within corresponding instance messages.|  
  
## See Also  
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)