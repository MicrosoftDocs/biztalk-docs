---
title: "Display the Contents of a Configuration File2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01695cef-8cba-466b-85d6-5398276ac6ab
caps.latest.revision: 4
---
# Display the Contents of a Configuration File
You can create a display of the entire contents of a configuration file by using the **/display** option with the following syntax:  
  
```  
  
[configpath]   
```  
  
 When you use the **/display** option, all the resources in the configuration file are displayed. For each resource, the display is the same as that from typing **snacfg** *resource* *resourcename*, where *resource* is the second word of a **snacfg** command (for example, **appcllu**, **connection**, or **server**), and *resourcename* is the name of the corresponding resource. (The exception to this is that the display of the "diagnostic" resource is the same as that from **snacfg diagnostic /list**.)  
  
## See Also  
 [Use the /print Option](../HIS2010/use-the-print-option2.md)   
 [General Syntax for the /print Option](../HIS2010/general-syntax-for-the-print-option1.md)   
 [Snacfg Reference](../HIS2010/snacfg-reference1.md)