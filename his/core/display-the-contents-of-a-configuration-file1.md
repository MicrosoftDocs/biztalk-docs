---
description: "Learn more about: Display the Contents of a Configuration File"
title: "Display the Contents of a Configuration File1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Display the Contents of a Configuration File
You can create a display of the entire contents of a configuration file by using the **/display** option with the following syntax:  
  
```  
  
[configpath]   
```  
  
 When you use the **/display** option, all the resources in the configuration file are displayed. For each resource, the display is the same as that from typing **snacfg** *resource* *resourcename*, where *resource* is the second word of a **snacfg** command (for example, **appcllu**, **connection**, or **server**), and *resourcename* is the name of the corresponding resource. (The exception to this is that the display of the "diagnostic" resource is the same as that from **snacfg diagnostic /list**.)  
  
## See Also  
 [Use the /print Option](../core/use-the-print-option1.md)   
 [General Syntax for the /print Option](../core/general-syntax-for-the-print-option2.md)   
 [Snacfg Reference](../core/snacfg-reference2.md)
