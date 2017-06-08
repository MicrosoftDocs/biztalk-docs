---
title: "&lt;Map File&gt; Property Page Dialog Box, Test Map Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.mapper.props.testmap"
helpviewer_keywords: 
  - "validating, BizTalk Mapper"
  - "validating, maps"
  - "testing, BizTalk Mapper"
  - "maps, testing"
  - "maps, validating"
  - "testing, maps"
  - "BizTalk Mapper, testing"
  - "BizTalk Mapper, validating"
ms.assetid: f0c35338-138e-47ad-9f41-19e017bd7d68
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# &lt;Map File&gt; Property Page Dialog Box, Test Map Tab
Use the **Test Map** tab on the **\<Map File> Property Page** dialog box to select files and file formats related to testing maps.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Validate TestMap Input**|Configure whether the input instance message being used to test the current map will be validated as conforming to its source schema prior to performing the mapping.|  
|**Validate TestMap Output**|Configure whether the output instance message that results from testing the current map will be validated as conforming to its destination schema after the mapping has been performed.|  
|**TestMap Input Instance**|Name the input instance message used to test the map.<br /><br /> Either type the path and name of the input instance message or use the ellipsis (**...**) button in this property value field to open the **Select Input File** dialog box, from which you can browse to the file you want.|  
|**TestMap Input**|Specify whether BizTalk Mapper will automatically generate an input instance message for use in testing the map, or if using an existing instance message, as specified by **TestMap Input Instance**, the format of that message (XML versus Native).|  
|**TestMap Output**|Specify the format (XML versus Native) of the output instance message generated when testing a map.|  
  
## See Also  
 [Validating Instance Data](../core/validating-instance-data.md)   
 [How to Test Maps](../Topic/How%20to%20Test%20Maps.md)   
 [How to Validate Maps](../Topic/How%20to%20Validate%20Maps.md)