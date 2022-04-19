---
description: "Learn more about: Value Parsing"
title: "Value Parsing1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44ac6268-2726-4426-8a45-0b445acf3a15
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Value Parsing
The following describes the syntax for value parsing for the Managed Provider for Host Files and provides an example.  
  
## Syntax  
 The primitive values are separated by commas. If there are complex data types like Unions or Arrays, then they are enclosed in curly brackets, like {value}.  
  
## Example  
 The following is an example of value parsing for the Managed Provider for Host Files.  
  
```  
("RECORD",{1234},{276578853},{1234},{271111111},{-1234},   
{-135363175},100,100,100)  
```  
  
## See Also  
 [SQL Parsing in the Managed Data Provider for Host Files](../core/sql-parsing-in-the-managed-data-provider-for-host-files2.md)
