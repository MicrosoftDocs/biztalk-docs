---
title: "WinAsyncCSV2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11e82472-577a-4b8f-84b3-c4c9423560f5
caps.latest.revision: 3
---
# WinAsyncCSV
The **WinAsyncCSV** function provides an asynchronous entry point for [TRANSFER_MS_DATA](../HIS2010/transfer-ms-data1.md) only. If this function is used for any other verb, the behavior will be synchronous. This function was used instead of the blocking version of the verb under Microsoft Windows version 3.*x*. Windows version 3.x is no longer supported.  
  
 HANDLE WINAPI WinAsyncCSV(  
  
## Syntax  
  
```  
  
    HWND hWnd,  
    long lpVcb  
);  
```  
  
#### Parameters  
 *hWnd*  
 Handle of window to receive message.  
  
 *lpVcb*  
 Pointer to the verb control block.  
  
## Return Value  
 The return value specifies whether the asynchronous resolution request was successful. If the function was successful, the return value is an asynchronous task handle. If the function was not successful, a zero is returned.  
  
## Remarks  
 When the asynchronous operation is complete, the applications window *hWnd* receives the message returned by **RegisterWindowMessage** with "WinAsyncCSV" as the input string. The *wParam* argument contains the asynchronous task handle returned by the original function call. The *lParam* argument contains the original VCB pointer and can be dereferenced to determine the final return code.  
  
 If the function returns successfully, a "WinAsyncCSV" message will be posted to the application when the operation completes or the conversation is canceled.