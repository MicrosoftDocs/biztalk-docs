---
title: "Windows LUA Considerations2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04cf13be-88fd-43a8-af93-5bfde264e9f3
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Windows LUA Considerations
The following Windows extensions are of particular importance and should be reviewed before using the logical unit application (LUA) application programming interface (API) and this version of [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]:  
  
-   [RUI](../core/rui1.md)  
  
     Provides event notification for all Request Unit Interface (RUI) verbs. The application must provide a handle to an event in the **lua_post_handle** member of the verb control block (VCB). The event must be in the not-signaled state. When the asynchronous operation is complete, the application is notified through the signaling of the event. Upon signaling of the event, examine the primary return code and secondary return code for any error conditions.  
  
-   [SLI](../core/sli1.md)  
  
     Provides event notification for all Session Level Interface (SLI) verbs. The application must provide a handle to an event in the **lua_post_handle** member of the VCB. The event must be in the not-signaled state. When the asynchronous operation is complete, the application is notified through the signaling of the event. Upon signaling of the event, examine the primary return code and secondary return code for any error conditions.  
  
-   [WinRUI](../core/winrui2.md)  
  
     Provides asynchronous notification for all Windows-based RUI verbs. When the asynchronous operation is complete, the application's window *hWnd* receives the message returned by **RegisterWindowMessage** with "WinRUI" as the input string. The *lParam* argument of the message contains the address of the VCB being posted as complete. The *wParam* argument of the message is undefined.  
  
     An application must call WinRUIStartup for initialization before calling WinRUI.  
  
-   [WinRUICleanup](../core/winruicleanup2.md)  
  
     An application must call this function when finished using RUI verbs to deregister itself from the Windows LUA implementation. This function terminates and deregisters an application from a Windows LUA implementation.  
  
-   [WinRUIStartup](../core/winruistartup2.md)  
  
     An application must call this function to register itself with a Windows LUA implementation before issuing any further Windows LUA calls using RUI verbs. This function allows an application to specify the version of Windows LUA required and to retrieve details of the specific LUA implementation.  
  
-   [WinSLI](../core/winsli2.md)  
  
     Provides asynchronous notification for all Windows-based SLI verbs. When the asynchronous operation is complete, the application's window *hWnd* receives the message returned by **RegisterWindowMessage** with "WinSLI" as the input string. The *lParam* argument of the message contains the address of the VCB being posted as complete. The *wParam* argument of the message is undefined.  
  
     An application must call WinSLIStartup for initialization before calling WinSLI.  
  
-   [WinSLICleanup](../core/winslicleanup1.md)  
  
     An application must call this function when finished using SLI verbs to deregister itself from the Windows LUA implementation. This function terminates and deregisters an application from a Windows LUA implementation.  
  
-   [WinSLIStartup](../core/winslistartup1.md)  
  
     An application must call this function to register itself with a Windows LUA implementation before issuing any further Windows LUA calls using SLI verbs. This function allows an application to specify the version of Windows LUA required and to retrieve details of the specific LUA implementation.