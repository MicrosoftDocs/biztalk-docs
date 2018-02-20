---
title: "Receiving Data Asynchronously1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe0387e3-97ee-4053-b242-0068db2a90e0
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Receiving Data Asynchronously
When using Windows, a TP can receive data asynchronously, without regard to other events occurring within the TP. The following table shows the methods by which a TP can receive data asynchronously. The table also indicates how asynchronous methods can be applied to actions other than receiving data.  
  
|Operating system|Method|  
|----------------------|------------|  
|Windows|**Through a Windows message:** Issue **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** with **WinAsyncAPPC**; the application is notified of completion through a **PostMessage** to the defined window handle.<br /><br /> This method is not restricted to **RECEIVE_AND_WAIT** and **MC_RECEIVE_AND_WAIT**, but can be applied to any APPC verb.|  
|Windows|**Through a Win32**® **event:** Issue **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** with **WinAsyncAPPCEx**; the application is notified of completion through a Win32 event.<br /><br /> This method is not restricted to **RECEIVE_AND_WAIT** and **MC_RECEIVE_AND_WAIT**, but can be applied to any APPC verb.|  
|Windows|With **RECEIVE_AND_POST** or **MC_RECEIVE_AND_POST:** Issue the **RECEIVE_AND_POST** or **MC_RECEIVE_AND_POST** verb.|  
  
 The following list gives details about these methods of receiving data asynchronously. For complete information, see the verb descriptions.  
  
 [RECEIVE_AND_WAIT](./receive-and-wait2.md)or [MC_RECEIVE_AND_WAIT](./mc-receive-and-wait2.md)with [WinAsyncAPPC](./winasyncappc1.md)  
 This method enables an application to issue a verb and be notified through a **PostMessage** when the action is complete. To retrieve the message number that will be posted to the window, call **RegisterWindowMessage** with "WinAsyncAPPC" as the input string. Then issue **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** using the **WinAsyncAPPC** entry point.  
  
 **RECEIVE_AND_WAIT**or **MC_RECEIVE_AND_WAIT**with [WinAsyncAPPCEx](./winasyncappcex1.md)  
 This method enables an application to be notified through a Win32 event. This is particularly useful when writing applications that need to service multiple conversations simultaneously. The event must be in the nonsignaled state when passed to APPC, and the handle must have EVENT_MODIFY_STATE access to the event.  
  
 [RECEIVE_AND_POST](./receive-and-post1.md)or [MC_RECEIVE_AND_POST](./mc-receive-and-post2.md)  
 When using **RECEIVE_AND_POST** or **MC_RECEIVE_AND_POST**, the application is notified through a Win32 event. The event must be in the nonsignaled state when passed to APPC, and the handle must have EVENT_MODIFY_STATE access to the event.  
  
 While receiving data asynchronously, the TP performs tasks not related to this conversation; the TP cannot issue most APPC verbs until notification is received. For information about the verbs that can be issued, see the descriptions of [WinAsyncAPPC](./winasyncappc1.md) or [WinAsyncAPPCEx](./winasyncappcex1.md).  
  
 After a verb has completed asynchronously, check the primary_rc to find out whether the data was received without error.  
  
> [!NOTE]
>  If the initial call to issue the verb returns successfully, the application is guaranteed to be notified (by the applicable method) when the verb completes, regardless of whether the verb is ultimately successful.