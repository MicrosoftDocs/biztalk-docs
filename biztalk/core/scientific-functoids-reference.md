---
title: "Scientific Functoids Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Scientific functoids, properties"
  - "functoid types, Scientific"
ms.assetid: e60738d7-9df9-4c73-91cc-692a6d481d4f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Scientific Functoids Reference
Use **Scientific** functoids to perform a variety of standard trigonometric, logarithmic, and exponential calculations.  
  
> [!IMPORTANT]
>  Because Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the underlying functionality of the .NET Framework, the results produced by some of the **Scientific** functoids may vary from the equivalent functoids in earlier versions of BizTalk Server. For example, very large values returned as output of these functoids may be returned as "Infinity" rather than an exponential value. You should test your maps thoroughly to ensure that you are getting the results you expect.  
  
 When a **Scientific** functoid determines that one or more of its input parameters is not valid, it cancels the operation and returns an empty string, such that a field in an output instance message is created as "\<FieldName>\</FieldName>" and the string [Size](../core/size-functoid.md) functoid returns zero (0).  
  
 When the input parameter descriptions specify a numeric value, strings that can be interpreted as numbers are also accepted.  
  
 For conceptual information about **Scientific** functoids, see [Scientific Functoids](../core/scientific-functoids.md).  
  
 The following table shows the functoids in the **Scientific** category.  
  
|Scientific functoid|Description|  
|-------------------------|-----------------|  
|![](../core/media/scientificexp10.gif "scientificexp10") [10^n](../core/10-n-functoid.md)|Returns the number 10 raised to a specified power.|  
|![](../core/media/scientificarctan.gif "scientificarctan") [Arc Tangent Functoid](../core/arc-tangent-functoid.md)|Returns the arc tangent of a number.|  
|![](../core/media/scientificlogn.gif "scientificlogn") [Base-Specified Logarithm](../core/base-specified-logarithm-functoid.md)|Returns the base-specified logarithm of a value.|  
|![](../core/media/scientificlog10.gif "scientificlog10") [Common Logarithm](../core/common-logarithm-functoid.md)|Returns the base 10 logarithm of a value.|  
|![](../core/media/scientificcos.gif "scientificcos") [Cosine](../core/cosine-functoid.md)|Returns the cosine of an angle.|  
|![](../core/media/scientificexp.gif "scientificexp") [Natural Exponential Function](../core/natural-exponential-functoid.md)|Returns **e** raised to a specified power.|  
|![](../core/media/scientificlog.gif "scientificlog") [Natural Logarithm](../core/natural-logarithm-functoid.md)|Returns the base **e** logarithm of a value.|  
|![](../core/media/scientificsin.gif "scientificsin") [Sine](../core/sine-functoid.md)|Returns the sine of an angle.|  
|![](../core/media/scientifictan.gif "scientifictan") [Tangent](../core/tangent-functoid.md)|Returns the tangent of an angle.|  
|![](../core/media/scientificpow.gif "scientificpow") [X^Y](../core/x-y-functoid.md)|Raises a specified value to the power of another specified value.|  
  
## See Also  
 [Scientific Functoids](../core/scientific-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)