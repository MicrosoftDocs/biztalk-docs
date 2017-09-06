---
title: "Error - First Input to Table Looping Functoid Not Valid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.firstInputForTableLoopingNotValid"
ms.assetid: 3ece2c0c-bcac-42d5-9536-34f073937879
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - First Input to Table Looping Functoid Not Valid
**Error Code**  
  
 btm1071  
  
 **Explanation**  
  
 The first input parameter to the relevant **Table Looping** functoid is not valid. This parameter must be a link from a node in the source schema—the number of occurrences of the corresponding element in an input instance message will control the number of times that the set of associated **Table Extractor** functoids will be invoked at run time.  
  
 **User Action**  
  
 Ensure that the input parameters to the **Table Looping** functoid, as accessed through the **Input Parameters** property and the **Configure \<Functoid> Functoid** dialog box, are as shown in the following table.  
  
|Table Looping functoid input parameter number|Description|  
|---------------------------------------------------|-----------------|  
|1|Link from a record or field in the source schema, the number of occurrences of which an input instance message controls the number of times the set of associated **Table Extractor** functoids are run.|  
|2|The number of columns in the data table configured through the **Table Looping Grid** property of the relevant **Table Looping** functoid.|  
|3 – 100|Constants and links (from the source schema or output from other functoids) that will become possible sources of data with the table looping grid.|