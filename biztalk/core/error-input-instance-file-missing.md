---
description: "Learn more about: Error - Input Instance File Missing"
title: "Error - Input Instance File Missing"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.inputInstanceFileMissing"
---
# Error - Input Instance File Missing
**Explanation**  
  
 No input instance message file has been specified, preventing the **Validate Instance** command from running.  
  
 **User Action**  
  
 Right-click the relevant schema file in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, and then click **Properties** to open the **Property Pages** dialog box for this schema. In this dialog box, on the **General** tab, click the ellipsis (**...**) button in the value field of the **Input Instance Filename** property, and then use the **Select Input File** dialog box to identify the file that contains the input instance message. You can also type the file name directly in the value field of the **Input Instance Filename** property.
