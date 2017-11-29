---
title: "How to Handle Errors While Creating a Link Service2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41b0ea53-dea1-497f-a0a9-0cd5d758d8a1
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Handle Errors While Creating a Link Service
As with most scripts, you need to write functions to handle any errors. This error handler scans the Windows Management Instrumentation (WMI) error queue for any relevant error information and posts and displays the error to the user.  
  
 The following sample shows how to handle errors while you are creating a link service:  
  
## Syntax  
  
```  
  
Sub PrintWMIErrorThenExit(strErrDesc, ErrNum)  
    On Error Resume Next  
    Dim objWMIError : Set objWMIError =    CreateObject("WbemScripting.SwbemLastError")  
    wscript.echo TypeName(objWMIError)  
  
    If ( TypeName(objWMIError) = "Empty" ) Then  
    wscript.echo strErrDesc & " (HRESULT: " & Hex(ErrNum) & ")."  
    Else  
    wscript.echo "Extended error information:"  
    wscript.echo objWMIError.Description  
    Set objWMIError = nothing  
    End If  
    Exit sub  
End Sub  
  
```