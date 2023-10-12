---
description: "Learn more about: Windows CSV Considerations]"
title: "Windows CSV Considerations]2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Windows CSV Considerations]
The following Microsoft® Windows® extensions are of particular importance and should be reviewed before using Windows CSV:  
  
 [WinAsyncCSV](./winasynccsv1.md)  
 Provides an asynchronous entry point for [TRANSFER_MS_DATA](./transfer-ms-data2.md) only. If used for any other verb, the behavior will be synchronous. Use this extension instead of the blocking version of the verb if you run your application under Microsoft® Windows® version 3.*x*.  
  
 When the asynchronous operation is complete, the application's window *hWnd* receives the message returned by **RegisterWindowMessage** with "WinAsyncCSV" as the input string. The *wParam* argument contains the asynchronous task handle returned by the original function call. The *lParam* argument contains the original verb control block (VCB) pointer and can be dereferenced to determine the final return code.  
  
 If the function returns successfully, a "WinAsyncCSV" message is posted to the application when the operation completes or the conversation is canceled.  
  
 [WinCSVCleanup](./wincsvcleanup1.md)  
 Terminates and deregisters an application from a Windows CSV implementation.  
  
> [!IMPORTANT]
>  An application must call this function to deregister itself from the Windows CSV implementation.  
  
 [WinCSVStartup](./wincsvstartup1.md)  
 Allows an application to specify the version of Windows CSV required and to retrieve details of the specific CSV implementation.  
  
> [!IMPORTANT]
>  An application must call this function to register itself with a Windows CSV implementation before issuing any further Windows CSV calls.
