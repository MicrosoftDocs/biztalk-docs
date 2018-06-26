---
title: "Standard Methods in Component Interfaces | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "component interfaces, standard methods"
  - "methods, viewing"
  - "methods, component interfaces"
  - "methods, changing"
ms.assetid: 2273d946-3fc8-4b2d-a6a1-9e4f0da74d5b
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Standard Methods in Component Interfaces
The standard methods for the component interface are as follows:  
  
- `Create`  
  
- `Find`  
  
- `Get`  
  
- `Save`  
  
  Only those methods in the underlying component are available. For example, if the underlying component does not contain `Add` capabilities, `Create` is unavailable.  
  
## Viewing or Changing Available Methods  
  
#### To view or change available methods  
  
1.  Open the component interface **Properties** dialog box.  
  
     ![](../core/media/psadapter-46-ps-properties.gif "PSAdapter_46_PS_Properties")  
  
2.  Click the **Standard Methods** tab.  
  
3.  Select the desired methods, and then click **OK**.  
  
## See Also  
 [How to Create Component Interfaces](../core/how-to-create-component-interfaces.md)   
 [Appendix C: Using Component Interfaces](../core/appendix-c-using-component-interfaces.md)