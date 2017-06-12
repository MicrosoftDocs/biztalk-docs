---
title: "How to Create a Map without Maps | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 520ec44f-5aca-4271-8835-b8e784214061
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a Map without Maps
If you have XSLT code you have been using to convert instance messages, you can use that code directly instead of creating a map.  
  
 Using your XSLT code involves creating an empty map and setting its **Custom XSLT Path** grid property. If your XSLT code uses external .NET assemblies, you will also need to create a custom extension XML file. For information about the structure of a custom extension XML file, see [Custom Extension XML (Grid Property)](../core/custom-extension-xml-grid-property.md).  
  
### To use custom XSLT code in place of a map  
  
1.  Create an empty BizTalk map in your project and set the source and destination schemas.  
  
     For information about creating the map and setting the schemas, see [Creating Maps](../core/creating-maps.md).  
  
2.  In the Grid view, click the mapper grid.  
  
     The Properties window shows the **Grid** properties.  
  
3.  In the Properties window, select **Custom XSLT Path** and click the ellipsis (**…**) button.  
  
4.  In the **Open** dialog box, navigate to the file and click **Open**.  
  
     The **Custom XSLT Path** property is set.  
  
> [!NOTE]
>  BizTalk Mapper supports XSLT 1.0 only. Using XSLT 2.0 in BizTalk Mapper is not supported.  
  
## See Also  
 [About Maps](../core/about-maps.md)   
 [Scripting Using Inline XSLT and XSLT Call Templates](../core/scripting-using-inline-xslt-and-xslt-call-templates.md)   
 [Custom XSLT](../core/custom-xslt.md)   
 [Custom XSLT Path (Grid Property)](../core/custom-xslt-path-grid-property.md)   
 [Custom Extension XML (Grid Property)](../core/custom-extension-xml-grid-property.md)