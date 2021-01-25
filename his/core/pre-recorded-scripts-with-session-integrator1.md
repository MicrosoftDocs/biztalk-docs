---
description: "Learn more about: Pre-Recorded Scripts with Session Integrator"
title: "Pre-Recorded Scripts with Session Integrator1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd8c2d14-5c5f-4e46-bcba-d90e67e67841
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Pre-Recorded Scripts with Session Integrator
The **SessionDisplayScript** class allows users to use a script created in the Host Integration Server 3270 client and play it programmatically.  
  
 The script can implement variables using a double percent sign on each end of the name, for example, %%MYVARIABLE%%. These variables are resolved using the SessionDisplayVariableCollection class provided in this class. In addition, the script file can contain environment variables using the standard notation which this class will translate.  
  
## SessionDisplayScript Class  
 The input script must be a normal text file with one command per line. The Script file supports the following commands:  
  
|Command|Description|  
|-------------|-----------------|  
|SETTIMEOUT {timeout},{label}|Sets the default timeout for all commands and the label where processing should continue. If no default is set, 30 seconds is assumed.|  
|WAITSESSION {wait}|Waits for the session to be in the input wait state before returning. The accepted values are: SSCP; LULU; UNOWNED|  
|WAIT {seconds}|Waits the input number of seconds and then moves to the next command. The WAIT command can be replaced by the WAITSTRING command to wait for a specific string on the screen.|  
|SETCURSOR {ROW},{COLUMN}|Moves the cursor to the desired position on the screen. If the position is not found on the screen, the script is aborted and a ScriptError Exception is returned with an InnerException of the actual Exception when running the script.|  
|SEND {string}, {%environmentvariable%}, {%%sessiondisplayvariable%%}|Causes the string to be sent to the screen using the SendKeys method. Variables can be input that are matched against the SessionDisplayVariablesCollection passed into the class. If a variable is not located in the script, the script is aborted and a ScriptError Exception is returned with a InnerException of Variable {name} not located in collection.|  
|GOTO {label}|Allows for scripts to jump to labels below the current line. If the label is not found, the script will abort with a ScriptError exception and an InnerException of “Label {name} not found”. {label} = A way to define a freeform label in the script that can be used in branching scenarios.|
