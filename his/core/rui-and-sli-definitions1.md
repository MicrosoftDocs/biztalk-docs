---
title: "RUI and SLI Definitions1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 717db68b-2bf6-4b2e-b310-2d63fd48ce75
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# RUI and SLI Definitions
The definitions of the [RUI](./rui2.md) and [SLI](./sli2.md) functions are as follows:  
  
```  
void WINAPI RUI(struct LUA_VERB_RECORD FAR * verb);  
void WINAPI SLI(struct LUA_VERB_RECORD FAR * verb);  
int WINAPI WinRUI(HWND handle, struct LUA_VERB_RECORD FAR * verb);  
int WINAPI WinSLI(HWND handle, struct LUA_VERB_RECORD FAR * verb);  
```  
  
 The WINLUA.H header file supplied with your Host Integration Server SDK includes prototypes of these functions.  
  
 The only parameter passed to the **RUI** or **SLI** function is the address of a verb control block (VCB). The VCB is a structure made up of variables that:  
  
- Identify the logical unit application (LUA) verb to be executed.  
  
- Supply information used by the verb.  
  
- Contain information returned by the verb when execution is complete.  
  
  The parameters passed to the [WinRUI](./winrui1.md)or [WinSLI](./winsli1.md) function are a window handle and the address of a VCB. The window handle is used for message notification when the issued verb has completed.  
  
  The VCB structure is declared in the WINLUA.H header file. For general VCB information, see [LUA VCB Format](../core/lua-vcb-format1.md). For verb-specific VCB information, see the reference documentation for each verb.