---
title: "How to Show and Hide Compiler Links | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66bfd9de-c4d2-46ee-854f-cf7c7cd07368
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Show and Hide Compiler Links
When you compile a map, BizTalk Mapper creates additional links, known as compiler links to account for all linking needed in the map. Some of these links are only implied by the links you created. When you compile, or test, a map, the final line in the Visual Studio Output window allows you to show or hide these additional compiler links in the main window. By default, the compiler links appear as red dashed lines.  
  
### To show or hide compiler links  
  
1. In Solution Explorer, right-click the map whose complier links you want to view, and then click **Test Map**.  
  
2. In the Visual Studio Error List window, scroll to the end and double-click the line that says **Double-click here to show/Hide compiler links**.  
  
    To change the display state of compiler links from shown to hidden, or from hidden to shown, just double-click that line again.  
  
   > [!NOTE]
   >  When you build/rebuild a BizTalk project or solution containing one or more maps, the message **Double-click here to show/Hide compiler links** is displayed in the **Error List** window of Visual Studio for all the maps in the project or solution.  
  
   To test a map, you must configure the properties for the input and output instances. For more information about how to configure these properties, see [How to Configure Map Validation and Test Parameters](../core/how-to-configure-map-validation-and-test-parameters.md).  
  
## See Also  
 [Using Links to Specify Record and Field Mappings](../core/using-links-to-specify-record-and-field-mappings.md)