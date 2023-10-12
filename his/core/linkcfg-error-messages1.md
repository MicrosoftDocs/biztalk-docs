---
description: "Learn more about: Linkcfg Error Messages"
title: "Linkcfg Error Messages1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Linkcfg Error Messages
The LinkCfg command utility returns the following codes and their corresponding messages. If you use the Windows Command Prompt, you only see the message. If you use Microsoft's System Management Server (SMS) to distribute link services across clients, you see the message and return code.  
  
|Error Code|Message|  
|----------------|-------------|  
|0|success.|  
|160|command-line arguments are invalid.|  
|1114|Unable to initialize Link Service DLL.|  
|1157|Unable to locate DLL file.|  
  
 In addition, LinkCfg will return error codes from GetLastError() calls for all file I/O operations.  
  
## See Also  
 [Linkcfg Reference](../core/linkcfg-reference2.md)
