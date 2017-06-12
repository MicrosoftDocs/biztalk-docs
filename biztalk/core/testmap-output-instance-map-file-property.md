---
title: "TestMap Output Instance (Map File Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7284f2e-5264-40e5-89b2-00b6b7aee771
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# TestMap Output Instance (Map File Property)
Use the **TestMap Output Instance** property to specify the location where the Test Map should generate the output message.  
  
## Category  
 Test Map  
  
## Allowed Values  
 Valid name of a file in which the output instance message will be stored by the Test Map.  
  
 Either type the full path name of the file or use the ellipsis (**...**) button on the right side of the input field to open the **Select Input File** dialog box.  
  
## Default Value  
 None.  
  
## Remarks  
 Configure this property if you want to generate output message in a custom location instead of default temp location. For more information about automatic generation of output instance messages versus providing a custom output instance message, see [TestMap Output (Map File Property)](../core/testmap-input-map-file-property.md).  
  
> [!NOTE]
>  Remember to set the **TestMap Output** property to XML or Native depending on the type of output message you want to generate.  
  
## See Also  
 [Map File Properties](../core/map-file-properties.md)