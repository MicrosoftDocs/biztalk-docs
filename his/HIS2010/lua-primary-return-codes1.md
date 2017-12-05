---
title: "LUA Primary Return Codes1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6cb80c5-2477-4b12-babf-7a8eb81e2fc8
caps.latest.revision: 3
---
# LUA Primary Return Codes
## 0x0000  
 LUA_OK  
 The verb executed successfully.  
  
## 0x0001  
 LUA_PARAMETER_CHECK  
 The verb did not execute because of a parameter error.  
  
## 0x0002  
 LUA_STATE_CHECK  
 The verb did not execute because it was issued in an invalid state.  
  
## 0x000F  
 LUA_SESSION_FAILURE  
 A required Microsoft® Host Integration Server component (such as the local node) has terminated.  
  
## 0x0014  
 LUA_UNSUCCESSFUL  
 The verb record supplied was valid, but the verb did not complete successfully.  
  
## 0x0018  
 LUA_NEGATIVE_RESPONSE  
 Either the logical unit application (LUA) sent a negative response to a message received from the primary logical unit (PLU) because an error was found in the message, or the application responded negatively to a chain for which the end-of-chain has arrived.  
  
## 0x0021  
 LUA_CANCELED  
 The secondary return code gives the reason for canceling the command.  
  
## 0x0030  
 LUA_IN_PROGRESS  
 An asynchronous command was received but is not completed.  
  
## 0x0040  
 LUA_STATUS  
 The secondary return code contains Session Level Interface (SLI) status information for the application.  
  
## 0xF003  
 LUA_COMM_SUBSYSTEM_ABENDED  
 Indicates one of the following conditions:  
  
-   The node used by this conversation encountered an ABEND.  
  
-   The connection between the transaction program (TP) and the physical unit (PU) 2.1 node was broken (a LAN error).  
  
-   The SnaBase at the TPs computer encountered an ABEND.  
  
## 0xF004  
 LUA_COMM_SUBSYSTEM_NOT_LOADED  
 A required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
## 0xF008  
 LUA_INVALID_VERB_SEGMENT  
 The verb control block (VCB) extended beyond the end of the data segment.  
  
## 0xF011  
 LUA_UNEXPECTED_DOS_ERROR  
 After issuing an operating system call, an unexpected operating system return code was received and is specified in the secondary return code.  
  
## 0xF015  
 LUA_STACK_TOO_SMALL  
 The stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
## 0xFFFF  
 LUA_INVALID_VERB  
 Either the verb code or the operation code, or both, is invalid. The verb did not execute.