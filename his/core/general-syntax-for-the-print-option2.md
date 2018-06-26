---
title: "General Syntax for the -print Option2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7016a1c9-83c0-47da-bf34-293640562361
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# General Syntax for the /print Option
The syntax lines in this section and the next section show ways to use the **/print** option. By default, the output is sent to the screen. To capture the output in a file, redirect it in the standard way, by adding a greater-than sign (>) to the end of the command, followed by the name of the file in which you want to capture the output.  
  
 With all the syntax lines, if the source configuration file is not in the default path \Program files\Host Integration Server\SYSTEM\CONFIG\COM.CFGthen for **#**<em>configpath</em>, substitute a path, preceded by the pound sign (**#**). Do not type the square brackets. After the greater-than sign (**>**), type the name of the command file you want to create. (For information about using the greater-than sign or other methods of redirection, see your Windows documentation.)  
  
 The general syntax for the **/print** option is:  
  
```  
  
[configpath] [resource [location]resourcename] cmdfile.ext  
```  
  
 For *resource*, substitute the second word of a **snacfg** command (for example, **appcllu**, **connection**, or **server**). For *location*, if needed, substitute the server or connection name that uniquely locates a resource; for *resourcename*, substitute the name of the resource.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)