---
title: "Functoid Categories | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BizTalk Mapper, functoids"
  - "functoids, categories"
ms.assetid: 029905e2-f01a-436a-b2ed-a364379c9cc5
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Functoid Categories
BizTalk functoids are divided into categories according to their intended use. For example, database functoids are designed for extracting data from a database at run time, mathematical functoids are used to perform mathematical operations, and so on. In BizTalk Mapper, functoids appear by category in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox. The following table shows the functoid categories, briefly describes the category, and shows the list of functoids in each category, including links to their corresponding reference pages.  
  
|Functoid category<br /><br /> Category description|Functoids in category|  
|------------------------------------------------|---------------------------|  
|**Advanced** ([Advanced Functoids Reference](../core/advanced-functoids-reference.md))<br /><br /> Primarily used with looping records. Also used for running arbitrary script or compiled code.|[Assert](../core/assert-functoid-reference.md), [Index](../core/index-functoid-reference.md), [Iteration](../core/iteration-functoid-reference.md), [Looping](../core/looping-functoid-reference.md), [Mass Copy](../core/mass-copy-functoid-reference.md), [Nil Value](../core/nil-value-functoid-reference.md), [Record Count](../core/record-count-functoid-reference.md), [Scripting](../core/scripting-functoid-reference.md), [Table Extractor](../core/table-extractor-functoid-reference.md), [Table Looping](../core/table-looping-functoid-reference.md), [Value Mapping](../core/value-mapping-functoid-reference.md), [Value Mapping (Flattening)](../core/value-mapping-flattening-functoid-reference.md)|  
|**Conversion** ([Conversion Functoids Reference](../core/conversion-functoids-reference.md))<br /><br /> Used to convert to and from ASCII, and between numeric bases.|[ASCII to Character](../core/ascii-to-character-functoid.md), [Character to ASCII](../core/character-to-ascii-functoid.md), [Hexadecimal](../core/hexadecimal-functoid.md), [Octal](../core/octal-functoid.md)|  
|**Cumulative** ([Cumulative Functoids Reference](../core/cumulative-functoids-reference.md))<br /><br /> Used to perform mathematical operations in looping records, such as averages and concatenation.|[Cumulative Average](../core/cumulative-average-functoid.md), [Cumulative Concatenate](../core/cumulative-concatenate-functoid.md), [Cumulative Maximum](../core/cumulative-maximum-functoid.md), [Cumulative Minimum](../core/cumulative-minimum-functoid.md), [Cumulative Sum](../core/cumulative-sum-functoid.md)|  
|**Database** ([Database Functoids Reference](../core/database-functoids-reference.md))<br /><br /> Used to extract data from a database and use it in destination instance messages.|[Database Lookup](../core/database-lookup-functoid.md), [Error Return](../core/error-return-functoid.md), [Format Message](../core/format-message-functoid.md), [Get Application ID](../core/get-application-id-functoid.md), [Get Application Value](../core/get-application-value-functoid.md), [Get Common ID](../core/get-common-id-functoid.md), [Get Common Value](../core/get-common-value-functoid.md), [Remove Application ID](../core/remove-application-id.md), [Set Common ID](../core/set-common-id-functoid.md), [Value Extractor](../core/value-extractor-functoid.md)|  
|**Date and Time** ([Date and Time Functoids Reference](../core/date-and-time-functoids-reference.md))<br /><br /> Used to retrieve the current date and time, and to calculate delta times.|[Add Days](../core/add-days-functoid.md), [Date](../core/date-functoid.md), [Date and Time](../core/date-and-time-functoid.md), [Time](../core/time-functoid.md)|  
|**Logical** ([Logical Functoids Reference](../core/logical-functoids-reference.md))<br /><br /> Used to perform a variety of logical operations, such as greater than and logical existence.|[Equal](../core/equal-functoid.md), [Greater Than](../core/greater-than-functoid.md), [Greater Than or Equal To](../core/greater-than-or-equal-to-functoid.md), [IsNil](../core/isnil-functoid.md), [Less Than](../core/less-than-functoid.md), [Less Than or Equal To](../core/less-than-or-equal-to-functoid.md), [Logical AND](../core/logical-and-functoid.md), [Logical Date](../core/logical-date-functoid.md), [Logical Existence](../core/logical-existence-functoid.md), [Logical Numeric](../core/logical-numeric-functoid.md), [Logical NOT](../core/logical-not-functoid.md), [Logical OR](../core/logical-or-functoid.md), [Logical String](../core/logical-string-functoid.md), [Not Equal](../core/not-equal-functoid.md)|  
|**Mathematical** ([Mathematical Functoids Reference](../core/mathematical-functoids-reference.md))<br /><br /> Used to perform a variety of mathematical operations, such as addition and multiplication.|[Absolute Value](../core/absolute-value-functoid.md), [Addition](../core/addition-functoid.md), [Division](../core/division-functoid.md), [Integer](../core/integer-functoid.md), [Maximum Value](../core/maximum-value-functoid.md), [Minimum Value](../core/minimum-value-functoid.md), [Modulo](../core/modulo-functoid.md), [Multiplication](../core/multiplication-functoid.md), [Round](../core/round-functoid.md), [Square Root](../core/square-root-functoid.md), [Subtraction](../core/subtraction-functoid.md)|  
|**Scientific** ([Scientific Functoids Reference](../core/scientific-functoids-reference.md))<br /><br /> Used to perform a variety of scientific operations, such as logarithms and trigonometry.|[10^n](../core/10-n-functoid.md), [Arc Tangent](../core/arc-tangent-functoid.md), [Base-Specified Logarithm](../core/base-specified-logarithm-functoid.md), [Common Logarithm](../core/common-logarithm-functoid.md), [Cosine](../core/cosine-functoid.md), [Natural Exponential Function](../core/natural-exponential-functoid.md), [Natural Logarithm](../core/natural-logarithm-functoid.md), [Sine](../core/sine-functoid.md), [Tangent](../core/tangent-functoid.md), [X^Y](../core/x-y-functoid.md)|  
|**String** ([String Functoids Reference](../core/string-functoids-reference.md))<br /><br /> Used to perform a variety of string functions, such as trimming and concatenation.|[Lowercase](../core/lowercase-functoid.md), [Size](../core/size-functoid.md), [String Concatenate](../core/string-concatenate-functoid.md), [String Extract](../core/string-extract-functoid.md), [String Find](../core/string-find-functoid.md), [String Left](../core/string-left-functoid.md), [String Left Trim](../core/string-left-trim-functoid.md), [String Right](../core/string-right-functoid.md), [String Right Trim](../core/string-right-trim-functoid.md), [Uppercase](../core/uppercase-functoid.md)|  
  
> [!NOTE]
>  The purpose of a functoid is usually obvious from its name.  
  
> [!NOTE]
>  All functoids included with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are inline C#, except for the **Database** functoids.  
  
## See Also  
 [Basic Functoids](../core/basic-functoids.md)   
 [Advanced Functoids](../core/advanced-functoids.md)