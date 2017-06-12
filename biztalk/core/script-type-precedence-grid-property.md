---
title: "Script Type Precedence (Grid Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Script Type Precedence property [grid pages]"
ms.assetid: 463c89fc-c389-436c-afc5-e6e31269141c
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Script Type Precedence (Grid Property)
Use the **Script Type Precedence** property to open the **Script Type Precedence** dialog box, in which you can configure the relative precedence of the various types of script. When the **Inline Script Buffer** edit box of the **Configure Functoid Script** dialog box contains script in multiple languages, the setting of this property controls which portions of script are run (only script in a single language is executed when a **Scripting** functoid is run).  
  
## Category  
 General  
  
## Allowed Values  
 The value of this property is an ordered list of script types, wherein each script type is either enabled or not. In the **Script Type Precedence** dialog box, use the up and down arrow buttons to change the relative order of the different types of scripts, where the script type at the top of the list has the highest precedence and the script type at the bottom of the list has the lowest precedence. Use the check box associated with each script type to specify whether that type of script is enabled. When a script is not enabled, its position in the list is irrelevant. The possible script types are:  
  
-   Inline C#  
  
-   External Assembly  
  
-   Inline Visual Basic .NET  
  
-   Inline JScript .NET  
  
-   Inline XSLT Call Template  
  
-   Inline XLST  
  
## Default Value  
 The following script types are all enabled by default, in the precedence order shown:  
  
1.  Inline C#  
  
2.  External Assembly  
  
3.  Inline Visual Basic .NET  
  
4.  Inline JScript .NET  
  
5.  Inline XSLT Call Template  
  
6.  Inline XLST  
  
## Remarks  
 Use the ellipsis [**...**] button on the right side of the input field to open the **Script Type Precedence** dialog box. In this dialog box, use the script type check boxes to enable or disable each particular type of script for this map, and use the up and down arrow buttons to rearrange the precedence order of the script types from highest to lowest.  
  
 Setting this property correctly is particularly important when one or more of your **Scripting** functoids has script in more than one language specified in the **Inline Script Buffer** edit box of the **Configure Functoid Script** dialog box. This can occur when you create script in one language, and then later change the inline scripting language and add new script in the new language without manually deleting the script written in the old language. In such cases, the precedence established by using this property determines which script is run during mapping.  
  
> [!NOTE]
>  You can undo or redo the **Script Type Precedence** property.  
  
## See Also  
 [Grid Properties](../core/grid-properties.md)