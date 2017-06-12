---
title: "TestMap Input (Map File Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TestMap Input property [map file]"
ms.assetid: ad11b72e-c9c1-4589-8f87-461cbf70e2c6
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# TestMap Input (Map File Property)
Use the **TestMap Input**property to specify the format of the input instance message specified by the **TestMap Input Instance** property, or to specify that you want to automatically generate an input instance message to use for testing the map.  
  
## Category  
 Test Map  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Generate Instance**|Use this value if you want an instance message to be generated automatically in the course of testing the map.|  
|**XML**|Use this value if the format of the input instance message specified by the **TestMap Input Instance** property is XML.|  
|**Native**|Use this value if the format of the input instance message specified by the **TestMap Input Instance** property is a native format, such as a flat file format, as specified by the source schema associated with the map.|  
  
## Default Value  
 **Generate Instance**  
  
## Remarks  
 If you specify a custom input instance message by using the **TestMap Input Instance** property, you must choose **XML** or **Native** as the value for this property. For more information, see [TestMap Input Instance (Map File Property)](../core/testmap-input-instance-map-file-property.md).  
  
## See Also  
 [Map File Properties](../core/map-file-properties.md)