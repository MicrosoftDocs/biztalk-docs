---
title: "Configure Functoid Script Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.mapper.functiod.script"
helpviewer_keywords: 
  - "scripts, Scripting functoids"
  - "BizTalk Mapper, Scripting functoids"
  - "Scripting functoids, BizTalk Mapper"
  - "BizTalk Mapper, functoids"
  - "functoids, BizTalk Mapper"
  - "functoids, mapping"
  - "BizTalk Mapper, scripts"
  - "scripts, BizTalk Mapper"
ms.assetid: 696dc165-0452-4b5b-83f4-2cbe814f175b
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure Functoid Script Dialog Box
Use the **Configure Functoid Script** dialog box to either identify or provide the code to be associated with the selected **Scripting** functoid.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Script Type**|Select this **Scripting** functoid as relying on an external assembly for its code, or select one of the available inline languages in which to provide your code within this dialog box. **Important:**  When you switch from one inline language to another, any script you have written for the language you are switching from is not deleted. You must either delete that script manually, or ensure that your new language choice has a higher precedence than your old language choice using the [Script Type Precedence Dialog Box](../core/script-type-precedence-dialog-box.md).|  
|**Script Assembly**|When **Script Type** has been set to External Assembly, select the assembly that contains the method to be used as the code for this functoid.|  
|**Script Class**|When **Script Type** has been set to External Assembly, select the class within the selected assembly that contains the method to be used as the code for this functoid.|  
|**Script Method**|When **Script Type** has been set to External Assembly, select the method within the selected assembly and class to be used as the code for this functoid.|  
|||  
|||  
  
## See Also  
 [Script Type Precedence Dialog Box](../core/script-type-precedence-dialog-box.md)   
 [How to Configure the Scripting Functoid](../core/how-to-configure-the-scripting-functoid.md)   
 [Scripting Functoid](../core/scripting-functoid.md)