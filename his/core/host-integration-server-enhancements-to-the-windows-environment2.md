---
description: "Learn more about: Host Integration Server Enhancements to the Windows Environment"
title: "Host Integration Server Enhancements to the Windows Environment2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Host Integration Server Enhancements to the Windows Environment
This section describes the extensions to Windows Advanced Program-to-Program Communications (APPC) and the Common Service Verb (CSV) API that are specific to Host Integration Server.  
  
 The [GetAppcConfig](../core/getappcconfig1.md) function takes a local logical unit (LU) and returns the remote LUs that are accessible to the user through that LU. If left blank, and a default local LU has been configured, the user's default local LU will be used. In all instances, if one of the returned remote LUs is the user's default, it is indicated as such.  
  
 The call is asynchronous and completion is normally signaled by the posting of a Microsoft Windows message. However, an alternative completion mechanism is provided for console applications.  
  
 The [GetAppcReturnCode](../core/getappcreturncode1.md) and [GetCsvReturnCode](../core/getcsvreturncode1.md) functions convert the primary and secondary return codes in the verb control block (VCB) to a printable string. These functions provide a standard set of error strings for use by applications.  
  
 For each extension, this section provides a definition of the function, syntax, returns, and remarks for using the function.  
  
## In This Section  
 [GetAppcConfig](../core/getappcconfig1.md)  
  
 [GetAppcReturnCode](../core/getappcreturncode1.md)  
  
 [GetCsvReturnCode](../core/getcsvreturncode1.md)
