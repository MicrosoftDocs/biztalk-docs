---
description: "Learn more about: How to Handle Errors While Creating a Link Service"
title: "How to Handle Errors While Creating a Link Service2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
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
