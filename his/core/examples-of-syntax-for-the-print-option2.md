---
description: "Learn more about: Examples of Syntax for the /print Option"
title: "Examples of Syntax for the -print Option2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Examples of Syntax for the /print Option
The following examples illustrate the use of the **/print** option.  
  
- To create a command file that can recreate an entire configuration file, type a command of the following form:  
  
  ```  
  
  [configpath] cmdfile.ext  
  ```  
  
- To create a command file from a particular connection in an existing configuration, type a command of the following form, substituting the name of the connection for *connectionname*:  
  
  ```  
  
  [configpath] connectionnamecmdfile.ext  
  ```  
  
- To create a command file from a particular 3270 LU in an existing configuration, type a command of the following form, substituting the name of the LU for *luname*:  
  
  ```  
  
  [configpath] lunamecmdfile.ext  
  ```  
  
  After generating **snacfg** command files, you can modify them and then use them like any other **snacfg** command file.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)
