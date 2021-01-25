---
description: "Learn more about: Error - Second Input for Table Extractor Functoid Not Valid"
title: "Error - Second Input for Table Extractor Functoid Not Valid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.secondInputForTableExtractorNotValid"
ms.assetid: 099f7374-8625-40af-a74b-24c4de941a7b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Second Input for Table Extractor Functoid Not Valid
**Error Code**  
  
 btm1073  
  
 **Explanation**  
  
 The second input parameter to the relevant **Table Extractor** functoid is not valid. This parameter must be a positive integer constant that indicates a valid column in the table looping grid configured for the **Table Looping** functoid that is indicated by the first input parameter.  
  
 **User Action**  
  
 Ensure that the input parameters to the relevant **Table Extractor** functoid, as accessed through its **Input Parameters** property and the **Configure \<Functoid\> Functoid** dialog box, are as shown in the following table.  
  
|Table Extractor functoid input parameter number|Description|  
|-----------------------------------------------------|-----------------|  
|1|Link from the **Table Looping** functoid from which this **Table Extractor** functoid will pull column data as indicated by its second parameter.|  
|2|The number of a valid column in the data table configured through the **Table Looping Grid** property of the **Table Looping** functoid specified by the first input parameter.|
