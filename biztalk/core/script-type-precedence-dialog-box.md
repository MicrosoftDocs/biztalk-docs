---
title: "Script Type Precedence Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.mapper.scripttype"
helpviewer_keywords: 
  - "BizTalk Mapper, Scripting functoids"
  - "Scripting functoids, BizTalk Mapper"
  - "functoids, scripts"
  - "scripts, functoids"
  - "functoids, BizTalk Mapper"
  - "scripts, BizTalk Mapper"
ms.assetid: 3369245f-d8af-4046-80db-757d8fb4916b
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Script Type Precedence Dialog Box
Use the **Script Type Precedence** dialog box to configure the relative precedence of the various types of script that can be associated with a **Scripting** functoid.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Inline C#**|Configure whether inline C# code is relevant in the precedence order established in this dialog box. **Note:**  Because the majority of functoids are written in C#, inline C# must remain enabled as an inline script language. Therefore, even if you clear the Inline C# check box, it will automatically become enabled again when you dismiss this dialog box.|  
|**External Assembly**|Configure whether code in external assemblies is relevant in the precedence order established in this dialog box.|  
|**Inline Visual Basic .NET**|Configure whether inline Microsoft Visual Basic .NET code is relevant in the precedence order established in this dialog box.|  
|**Inline JScript .NET**|Configure whether inline Microsoft Visual JScript .NET code is relevant in the precedence order established in this dialog box.|  
|**Inline XSLT Call Template**|Configure whether inline XSLT Call Template code is relevant in the precedence order established in this dialog box.|  
|**Inline XSLT**|Configure whether inline XSLT code is relevant in the precedence order established in this dialog box.|  
|**Move selected script type up button**<br /><br /> ![](../core/media/bts-tls-paramup.gif "bts_tls_paramup")|Exchange the selected script type with the script type immediately above it in the ordered list, increasing the relative precedence of the selected script type.|  
|**Move selected script type down button**<br /><br /> ![](../core/media/bts-tls-paramdown.gif "bts_tls_paramdown")|Exchange the selected script type with the script type immediately below it in the ordered list, decreasing the relative precedence of the selected script type.|  
  
## See Also  
 [Configure Functoid Script Dialog Box](../core/configure-functoid-script-dialog-box.md)   
 [How to Configure the Scripting Functoid](../core/how-to-configure-the-scripting-functoid.md)   
 [Scripting Functoid](../core/scripting-functoid.md)