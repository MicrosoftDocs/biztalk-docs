---
title: "TestMap Input Instance (Map File Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TestMap Input Instance property [map file]"
ms.assetid: 403f5c2f-bc89-46a4-a309-4841172c4b45
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# TestMap Input Instance (Map File Property)
Use the **TestMap Input Instance** property to configure the location of the input instance message file to be used to test the map.  
  
## Category  
 Test Map  
  
## Allowed Values  
 Valid name of a file that contains the instance message that you want to use when testing the map.  
  
 Either type the full path name of the file or use the ellipsis (**...**) button on the right side of the input field to open the **Select Input File** dialog box.  
  
## Default Value  
 None.  
  
## Remarks  
 Configure this property if you want to test your map by using a custom instance message rather than an instance message generated automatically by BizTalk Mapper. For more information about automatic generation of input instance messages versus providing a custom input instance message, see [TestMap Input (Map File Property)](../core/testmap-input-map-file-property.md).  
  
> [!NOTE]
>  Remember to set the **TestMap Input** property to XML. Otherwise BizTalk will continue to generate an input instance message rather than using the file you specified.  
  
## See Also  
 [Map File Properties](../core/map-file-properties.md)