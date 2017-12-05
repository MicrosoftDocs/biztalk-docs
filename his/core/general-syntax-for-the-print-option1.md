---
title: "General Syntax for the -print Option1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb594d4e-9b6e-4464-ba55-eda01fe57245
caps.latest.revision: 3
---
# General Syntax for the /print Option
The syntax lines in this section and the next section show ways to use the **/print** option. By default, the output is sent to the screen. To capture the output in a file, redirect it in the standard way, by adding a greater-than sign (>) to the end of the command, followed by the name of the file in which you want to capture the output.  
  
 With all the syntax lines, if the source configuration file is not in the default path \Program files\Host Integration Server\SYSTEM\CONFIG\COM.CFGthen for **#***configpath*, substitute a path, preceded by the pound sign (**#**). Do not type the square brackets. After the greater-than sign (**>**), type the name of the command file you want to create. (For information about using the greater-than sign or other methods of redirection, see your Windows documentation.)  
  
 The general syntax for the **/print** option is:  
  
```  
  
[configpath] [resource [location]resourcename] cmdfile.ext  
```  
  
 For *resource*, substitute the second word of a **snacfg** command (for example, **appcllu**, **connection**, or **server**). For *location*, if needed, substitute the server or connection name that uniquely locates a resource; for *resourcename*, substitute the name of the resource.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference1.md)