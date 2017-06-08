---
title: "Logical Functoids Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Logical functoids, about Logical functoids"
  - "Logical functoids, properties"
  - "functoid types, Logical"
ms.assetid: e64b6106-4ac1-460e-b214-f655820428bd
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Logical Functoids Reference
Use **Logical** functoids to perform a variety of logical operations, often controlling whether a particular element or attribute is created in an output instance message.  
  
> [!IMPORTANT]
>  Because Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the underlying functionality of the .NET Framework, the results produced by some of the **Logical** functoids may vary from the equivalent functoids in earlier versions of BizTalk Server. For example, **Logical** functoids are case-sensitive when comparing two strings: "Abc" and "abc" are not equal. The exception to this rule is when **Logical** functoids compare strings that represent the Boolean values **True** and **False**:"True" and "true" are equal. You should test your maps thoroughly to ensure that you are getting the results you expect.  
  
 Unless otherwise noted, **Logical** functoids always output a Boolean value, either **True** or **False**. This means that you cannot use the output of a **Logical** functoid as the input to a functoid that is expecting a string, such as the **Uppercase** functoid, hoping to yield an output string like "TRUE". In other words, you should not connect the output of a logical functoid to a node and expect that field to be populated with a string value of "TRUE" or "FALSE" or variant ("True", "true", "False", "false", etc).  
  
 On the other hand, **Logical** functoids do accept a few different data types (Boolean values, strings, and numbers) as input values. They use standard semantics to interpret and compare such values. The best practice is to pass two parameters of the same data type, which results in the following actions:  
  
-   When both input parameters are Boolean values, a logical comparison is performed.  
  
-   When both input parameters are numbers, both are converted to Boolean values where non-zero values become Boolean **True** and zero values become Boolean **False**, followed by a logical comparison.  
  
-   When both input parameters are strings, a case-sensitive string comparison is performed. If appropriate, use either the [Uppercase](../core/uppercase-functoid.md) or [Lowercase](../core/lowercase-functoid.md) functoid to force both input strings to the same case. Note that passing strings to the **Logical AND**, **Logical NOT**, and **Logical OR** functoids does not yield meaningful results.  
  
 The following two obscure cases are also supported:  
  
-   If one input parameter is a number and the other input parameter is a string, a case-sensitive string comparison is performed. This means that the string needs to be a string version of a number for the comparison to be meaningful.  
  
-   If one input parameter is Boolean and the other input parameter is a string, use the literal string "true" (case-sensitive) to represent the Boolean value **True** and the literal string "false" (case-sensitive) to represent the Boolean value **False**. Other string values for **True** and **False** are not supported for all **Logical** functoids, including differences in case only.  
  
 Passing a Boolean input parameter and a numeric input parameter is not supported in a meaningful way.  
  
 For conceptual information about **Logical** functoids, see [Logical Functoids](../core/logical-functoids.md).  
  
> [!IMPORTANT]
>  When the output of any logical functoid is directly linked to a target schema node, on doing a test map, you do not get a logical value (true/false) as the output. It is rendered as blank. Therefore, the output of a logical value should be connected only to those functoids which accept logical input parameters.  
  
 The following table shows the functoids in the **Logical** category.  
  
|Logical functoid|Description|  
|----------------------|-----------------|  
|![](../core/media/logicaleq.gif "logicaleq") [Equal](../core/equal-functoid.md)|Tests whether the two input parameters are equal.|  
|![](../core/media/logicalgt.gif "logicalgt") [Greater Than](../core/greater-than-functoid.md)|Tests whether the first input parameter is greater than the second input parameter.|  
|![](../core/media/logicalgte.gif "logicalgte") [Greater Than or Equal To](../core/greater-than-or-equal-to-functoid.md)|Tests whether the first input parameter is greater than or equal to the second input parameter.|  
|![Logical IsNil functoid](../core/media/logical-isnil-functoid.gif "logical_isnil_functoid") [IsNil](../core/isnil-functoid.md)|Test whether the input parameter is Nil.|  
|![](../core/media/logicallessthan.gif "logicallessthan") [Less Than](../core/less-than-functoid.md)|Tests whether the first input parameter is less than the second input parameter.|  
|![](../core/media/logicallte.gif "logicallte") [Less Than or Equal To](../core/less-than-or-equal-to-functoid.md)|Tests whether the first input parameter is less than or equal to the second input parameter.|  
|![](../core/media/logicaland.gif "logicaland") [Logical AND](../core/logical-and-functoid.md)|Determines whether all of the specified input parameters are true.|  
|![](../core/media/logicalisdate.gif "logicalisdate") [Logical Date](../core/logical-date-functoid.md)|Determines whether the input parameter is a date.|  
|![](../core/media/logicalexistence.gif "logicalexistence") [Logical Existence](../core/logical-existence-functoid.md)|Determines whether the record or field that is linked to it exists in a particular source instance message.|  
|![Logical NOT functoid](../core/media/logical-not-functoid.gif "logical_not_functoid") [Logical NOT](../core/logical-not-functoid.md)|Returns the logical inverse of the input parameter.|  
|![](../core/media/logicalisnumeric.gif "logicalisnumeric") [Logical Numeric](../core/logical-numeric-functoid.md)|Determines whether the input parameter is a numeric value.|  
|![](../core/media/logicalor.gif "logicalor") [Logical OR](../core/logical-or-functoid.md)|Determines whether any of the specified input parameters are true.|  
|![](../core/media/logicalisstring.gif "logicalisstring") [Logical String](../core/logical-string-functoid.md)|Determines whether the input parameter is a string.|  
|![](../core/media/logicalnotequal.gif "logicalnotequal") [Not Equal](../core/not-equal-functoid.md)|Tests whether the two input parameters are not equal.|  
  
## See Also  
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)