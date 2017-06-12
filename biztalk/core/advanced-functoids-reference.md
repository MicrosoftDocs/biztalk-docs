---
title: "Advanced Functoids Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "functoid types, Advances"
  - "Advanced functoids"
ms.assetid: 4b7a761f-510c-47ce-9506-4cb8e9ebba5c
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Advanced Functoids Reference
Use **Advanced** functoids to create various types of data manipulation, such as implementing custom script, value mapping, and managing and extracting data from looping records.  
  
 For conceptual information about **Advanced** functoids, see [Advanced Functoids](../core/advanced-functoids.md).  
  
 The following table shows the functoids in the **Advanced** category.  
  
|Advanced functoid|Description|  
|-----------------------|-----------------|  
|![Assert functoid](../core/media/advanced-assert-functoid.gif "advanced_assert_functoid") [Assert](../core/assert-functoid-reference.md)|Enables you to test your assumptions about conditions in a map. Assertions are tested in Development builds only.|  
|![](../core/media/advindex.gif "advindex") [Index](../core/index-functoid-reference.md)|Provides a way to extract a particular value from a sequence of repeating values by specifying the appropriate index. Indices can also have varying degrees of scope depending on hierarchy depth and levels indicated by the index.|  
|![](../core/media/adviteration.gif "adviteration") [Iteration](../core/iteration-functoid-reference.md)|For each repetition of a structure or value in an input instance message, outputs a monotonically increasing index.|  
|![](../core/media/advlooping.gif "advlooping") [Looping](../core/looping-functoid-reference.md)|Used to explicitly indicate a looping relationship between a repeating structure in the source schema and a repeating structure in the destination schema.|  
|![](../core/media/advmasscopy.gif "advmasscopy") [Mass Copy](../core/mass-copy-functoid-reference.md)|Recursively copies all data in an input instance message, to arbitrary depth, that corresponds to a specified node in the source schema to the specified position in an output instance message.|  
|![Nil Value functoid](../core/media/advanced-nil-value-functoid.gif "advanced_nil_value_functoid") [Nil Value](../core/nil-value-functoid-reference.md)|Sets the value of the destination node to **Nil**.|  
|![](../core/media/advcount.gif "advcount") [Record Count](../core/record-count-functoid-reference.md)|Outputs the number of times a specified repeating structure or value occurs in an input instance message.|  
|![](../core/media/advscript.gif "advscript") [Scripting](../core/scripting-functoid-reference.md)|Runs custom script to create content for an output instance message or input to another functoid.|  
|![](../core/media/advtableextractor.gif "advtableextractor") [Table Extractor](../core/table-extractor-functoid-reference.md)|Outputs the data associated with a specified column for each row of the table looping grid of a **Table Looping** functoid.|  
|![](../core/media/advtablelooping.gif "advtablelooping") [Table Looping](../core/table-looping-functoid-reference.md)|In conjunction with one or more **Table Extractor** functoids, creates a repeating structure in an output instance message by using constant values, values from an instance message, and values that are output from other functoids.|  
|![](../core/media/advvaluemap.gif "advvaluemap") [Value Mapping](../core/value-mapping-functoid-reference.md)|Allows a Boolean value to control whether an entire structure or another single value in an input instance message gets copied to an output instance message.|  
|![](../core/media/advvaluemapflattening.gif "advvaluemapflattening") [Value Mapping (Flattening)](../core/value-mapping-flattening-functoid-reference.md)|Allows a Boolean value to control whether an entire structure in an input instance message gets copied to an output instance message, flattening the input hierarchy in the process.|  
  
## See Also  
 [Adding Advanced Functoids to a Map](../core/adding-advanced-functoids-to-a-map.md)