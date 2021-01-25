---
description: "Learn more about: Linkcfg Error Messages"
title: "Linkcfg Error Messages1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef50ff69-c0b9-4794-a5c1-0fcfd9849726
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
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
