---
title: "How TI Enables TPs to Return Exceptions1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7be55091-1883-4a8d-b906-e885211beb4a
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How TI Enables TPs to Return Exceptions
TI provides a Meta data mechanism for returning exceptions from Automation server applications like TI applications. TI uses this mechanism to provide the mainframe developer with an optional way to return mainframe error information (also known as exception data) back through the normal application.  
  
 A transaction program (TP) returns error information as optional Meta data that includes an exception block as part of the reply message. The exception block contains information, in a standard format, that can be used to populate an Automation exception structure.  
  
 TI error messages have numbers in the range 0-9999. Meta data error message numbers returned from the mainframe can fall within the same range. To distinguish TI error messages from Meta data messages returned from the mainframe, TI adds 10000 to the number of any Meta data error message returned from the mainframe.  
  
 A TP can also use this mechanism to provide information regarding the TP state to the TI run-time environment. Specifically, a TP can indicate whether the TP:  
  
- Is willing to commit the work performed so far (and deallocate the conversation).  
  
- Can perform no more work on the current conversation and expects the client to prepare and commit.  
  
- Has encountered an error that will prevent it from committing the transaction.  
  
  While it is always possible for a TP to deallocate the conversation abruptly, TI exceptions allow it to return detailed information about the error to the calling client application.  
  
  TI uses the information contained in the exception block to update state information in the TI run-time environment and (if requested) return an exception to the client application.  
  
  The following table shows the fields in the EXCEPINFO exception structure.  
  
|Field|Description|  
|-----------|-----------------|  
|*wCode*|The error code returned in the exception block.|  
|*bstrSource*|Generated automatically by TI based on information about the customer's object and the remote TP.|  
|*bstrDescription*|From the exception block. This error description comes from the remote TP.|  
|*bstrHelpFile*|Formed by taking the Help path associated with the object's component library (in the Registry) and combining it with an unqualified file name included as custom information in the component library. This allows the developer to identify the file name of the Help file as it was created, while giving the administrator ultimate control over where the Help file is installed during deployment.|  
|*dwHelpContext*|From the exception.|  
|*scode*|Same as *wCode*.|  
  
 It is possible for the TP to return state information without actually raising an exception. To keep the mainframe TP code as straightforward as possible, the exception data is part of the optional Meta data and is returned in all cases, whether an error occurs or not.  
  
## See Also  
 [What WIP Does](../core/what-wip-does1.md)