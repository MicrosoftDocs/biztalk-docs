---
title: "Primary CSV Return Codes2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13606d7e-f60a-4752-af2b-850982ee5248
caps.latest.revision: 3
---
# Primary CSV Return Codes
## 0000  
 SV_OK  
 The verb executed successfully.  
  
## 0001  
 SV_PARAMETER_CHECK  
 The verb did not execute because of a parameter error.  
  
## 0002  
 SV_STATE_CHECK  
 The verb did not execute because it was issued in an invalid state.  
  
## 0021  
 SV_CANCELLED  
 This code is returned for an asynchronous verb when it has been shut down by a [WinCSVCleanup](../core/wincsvcleanup.md) call.  
  
## 0030  
 SV_FILE_ALREADY_EXISTS  
 When the SV_NEW file option was used, the file name specified was the name of an existing file.  
  
## 0031  
 SV_OUTPUT_DEVICE_FULL  
 There is insufficient space on the device where the output file resides. Retry the operation after freeing additional disk space.  
  
## F006  
 SV_THREAD_BLOCKING  
 This verb exceeds the maximum number of simultaneous synchronous verbs allowed.  
  
## F008  
 SV_INVALID_VERB_SEGMENT  
 The verb control block (VCB) extended beyond the end of the data segment.  
  
## F011  
 SV_UNEXPECTED_DOS_ERROR  
 One of the following conditions occurred:  
  
-   The Microsoft Windows system encountered an error while processing the verb. The operating system return code was returned through the secondary return code. If the problem persists, contact the system administrator for corrective action.  
  
-   A CSV was issued from a message loop that was invoked by another application issuing a Windows environment **SendMessage** function call, rather than the more common Windows environment **PostMessage** function call. Verb processing cannot take place.  
  
-   A CSV was issued when **SendMessage** invoked your application. You can determine whether your application has been invoked with **SendMessage** by using the **InSendMessage** Windows API function call.  
  
## F012  
 SV_COMM_SUBSYSTEM_NOT_LOADED  
 A required component could not be loaded or has terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
## F024  
 SV_SERVER_RESOURCE_NOT_FOUND  
 No communication server was found that could provide the requested function.  
  
## F026  
 SV_SERVER_RESOURCE_LOST  
 The communications server that was providing the function was lost due to a connection failure.  
  
## FFFF  
 SV_INVALID_VERB  
 The **opcode** parameter did not match the operation code of any verb. No verb executed.