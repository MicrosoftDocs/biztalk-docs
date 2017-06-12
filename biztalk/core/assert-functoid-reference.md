---
title: "Assert Functoid Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6fa11fc8-1fd2-403e-a961-f67714781aa6
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Assert Functoid Reference
The **Assert** functoid (![Assert functoid](../core/media/advanced-assert-functoid.gif "advanced_assert_functoid")) enables you to test your assumptions about conditions in your map. For example, if you perform some calculations to determine an additional discount on product purchases, you might assert that the additional discount be no more than $100 by using a logical functoid (**Greater Than** or **Less Than**).  
  
## Input  
 **Parameter 1:** A Boolean value, generally from the output of some other **Logical** functoid or from a variable Boolean field in the input instance message.  
  
 **Parameter 2:** Text to use when throwing an exception if Parameter 1 is **False**. This should be a descriptive statement that can be used to locate the source of the failed assertion.  
  
 **Parameter 3:** Text to return if the Parameter 1 is **True**.  
  
## Output  
 **Output 1:** The text value of **Parameter 3** if Parameter 1 is **True**; otherwise, the functoid throws an exception.  
  
## Remarks  
 The **Assert** functoid only fires in development builds or when the **Generate Debugging Information**property in the project build settings is set to **True**. When your BizTalk Server application is compiled for deployment and the **Generate Debugging Information** property is set to **False** (the default), assertions are ignored.  
  
> [!NOTE]
>  Balance the need for **Assert** functoid processing in production builds with the additional overhead that may be required to process them.  
  
## See Also  
 [Advanced Functoids Reference](../core/advanced-functoids-reference.md)   
 [Advanced Functoids](../core/advanced-functoids.md)