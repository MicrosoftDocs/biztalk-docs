---
title: "RUI2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82511e4e-133d-448a-8bf8-0c0aaa1055aa
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# RUI
The **RUI** function provides event notification for all Request Unit Interface (RUI) verbs.  
  
## Syntax  
  
```  
  
          void WINAPI RUI(   
LUA_VERB_RECORD FAR *lpVCB  );  
```  
  
#### Parameters  
 *lpVCB*  
 Pointer to the logical unit application (LUA) verb control block (VCB), **LUA_VERB_RECORD**.  
  
## Return Value  
 The code returned in **lua_prim_rc** indicates whether asynchronous notification will occur. If the field is set to LUA_IN_PROGRESS, asynchronous notification will occur through event signaling. If the flag is not LUA_IN_PROGRESS, the request completed synchronously. Examine the primary return code and secondary return code for any errors.  
  
## Remarks  
 The application must provide a handle to an event in the **lua_post_handle** parameter of the VCB. The event must be in the not-signaled state.  
  
 When the asynchronous operation is complete, the application is notified through the signaling of the event. Upon signaling of the event, examine the primary return code and secondary return code for any error conditions.  
  
## See Also  
 [WinRUI](../core/winrui1.md)