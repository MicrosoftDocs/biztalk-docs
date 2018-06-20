---
title: "How to Debug Maps | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1ee1e26-fced-4126-b48a-71007043424d
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Debug Maps
The **Debug Map** feature is useful in identifying and fixing complex mapping issues. This topic provides step-by-step instructions for debugging maps using the inline XSLT debugger.  

> [!NOTE]
>  When debugging the map, the **Debug Map** feature uses the map file properties **TestMap Input Instance** and **TestMap Output Instance**. Therefore, before you debug the map, we recommend that you configure the input and output instance properties in the map file.  

### To debug a BizTalk map  

1. In Solution Explorer, right-click the map you want to test, and then click **Debug Map**. [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] displays the map in XSLT format in its editor.  

2. Press F10 or F11 to debug the XSL code. When you press F11 on a functoid call, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] steps into the C# code for the functoid. You can view the values of variables used in the functoid source code in the Local Windows Debugger.
