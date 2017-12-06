---
title: "SLI2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5f2b1edb-abd8-48bc-9c09-9ec05a43faf5
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# SLI
The **SLI** function provides event notification for all Session Level Interface (SLI) verbs.  
  
## Syntax  
  
```  
  
          void WINAPI SLI(   
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
 [WinSLI](../core/winsli.md)