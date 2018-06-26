---
title: "Use a Command File1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8397f7c-199c-49e3-88b8-003150853045
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Use a Command File
If you want to run a series of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] configuration commands, you can remove the word **snacfg** from each command, place the new commands in a file called a command file, then use a single **snacfg** command to run the entire command file. This is similar to the way a batch file works; however, a command file opens and closes the configuration file fewer times than a batch file. When a command file is run, the configuration file is opened only once, at the beginning. Then all the commands are carried out, and the configuration file is closed. In contrast, when a batch file containing **snacfg** commands is run, the configuration file is opened and closed multiple times, once for every command in the file.  
  
 When creating a command file, do not include the following:  
  
- The word **snacfg**  
  
- A path for a configuration file  
  
- A command path for another command file  
  
- A backslash inside the text string for a comment  
  
  Also, you can include long, multiline commands in a command file by ending lines with a backslash ( \ ). The backslash indicates that the string in the next line should be appended to the current command.  
  
  There are two steps for using a command file. First, create the file, either by typing the configuration commands into a plain text file, or by using the **/print** option as described in the next section. Then run the command file from the command prompt by typing a line with the following syntax:  
  
```  
  
[configpath]commandpath []  
  
```  
  
 In the preceding syntax line, *configpath* is the path of the configuration file on which commands should be carried out; precede this path with the **#** symbol. Similarly, *commandpath* is the path of the command file; precede this path with the **@** symbol. Use the **/v** (verbose) option to cause all informational messages (not just error messages) to be displayed when the command file is running. Without the **/v** option, only error messages are displayed.  
  
 For example, to run a series of commands that result in a listing of the links and connections in a configuration file, create a file called SNA_CMD1.TXT, containing the following lines:  
  
```  
link /list  
connection /list  
```  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)