---
title: "Script (Functoid Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Scripting functoids, scripts"
  - "functoids, scripts"
  - "Scripting functoids, configuring"
  - "Script property [functoids]"
ms.assetid: 083334f8-2aa2-4054-9d11-6174b546156c
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Script (Functoid Property)
Use the **Script** property to open the **Configure Functoid Script** dialog box, in which you can configure the custom script or compiled code to be associated with the corresponding **Scripting** functoid.  
  
## Category  
 General  
  
## Value  
 The value of this property is the collection of values configured in the **Configure Functoid Script** dialog box. This includes an appropriate combination of values for the following fields in that dialog box:  
  
-   **Script Type.** Set to either **Inline C#**, **External Assembly**, **Inline JScript .NET**, **Inline Visual Basic .NET**, **Inline XSLT**, or **Inline XSLT Call Template**.  
  
    > [!IMPORTANT]
    >  When you switch from one inline language to another, any script you have written for the language you are switching from is not deleted. You must either delete that script manually, or make sure that your new language choice has a higher precedence than your old language choice by using the [Script Type Precedence](../core/script-type-precedence-grid-property.md) grid property.  
  
-   **Script Assembly.** Must be set when **Script Type** is set to **External Assembly**.  
  
-   **Script Class.** Must be set when **Script Type** is set to **External Assembly**.  
  
-   **Script Method.** Must be set when **Script Type** is set to **External Assembly**.  
  
## Remarks  
 This property is only available for the **Scripting** functoid, and is not enabled when any other type of functoid is selected.  
  
## See Also  
 [General Functoid Properties](../core/general-functoid-properties.md)