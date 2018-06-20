---
title: "Examples of Syntax for the -print Option2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02ba271f-ff56-4a42-8c62-8684d33c6b18
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
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