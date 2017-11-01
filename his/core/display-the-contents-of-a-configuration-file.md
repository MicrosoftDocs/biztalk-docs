---
title: "Display the Contents of a Configuration File1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ded1cb5d-8433-46dd-9ce0-d9ead39b75a9
caps.latest.revision: 4
---
# Display the Contents of a Configuration File
You can create a display of the entire contents of a configuration file by using the **/display** option with the following syntax:  
  
```  
  
[configpath]   
```  
  
 When you use the **/display** option, all the resources in the configuration file are displayed. For each resource, the display is the same as that from typing **snacfg** *resource* *resourcename*, where *resource* is the second word of a **snacfg** command (for example, **appcllu**, **connection**, or **server**), and *resourcename* is the name of the corresponding resource. (The exception to this is that the display of the "diagnostic" resource is the same as that from **snacfg diagnostic /list**.)  
  
## See Also  
 [Use the /print Option](../core/use-the-print-option.md)   
 [General Syntax for the /print Option](../core/general-syntax-for-the-print-option.md)   
 [Snacfg Reference](../core/snacfg-reference.md)