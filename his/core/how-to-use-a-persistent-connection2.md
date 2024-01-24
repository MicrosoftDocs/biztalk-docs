---
description: "Learn more about: How To Use a Persistent Connection"
title: "How To Use a Persistent Connection2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How To Use a Persistent Connection
The following topic describes how to use a persistent connection with Windows-Initiated Processing (WIP)  
  
### To use a persistent connection with WIP  
  
1.  Set the COMTIContext keyword CONNTYPE to OPEN.  
  
     If a call with CONNTYPE set to OPEN completes successfully, the returned COMTIContext array CONNTYPE keyword will have a value of USE.  
  
     After you set the COMTIContext keyword CONNTYPE to OPEN, you can choose to set CONNTYPE to USE. However, this action is not mandatory because it is set to USE by default.  
  
2.  Once you have established the connection, you can use the COMTIContext object to access the mainframe.  
  
3.  If the method call fails, use UpdateContextInfo and GetConnectionInfo on the COMTIContextLib.ContextObject to obtain updated status of the connection.  
  
4.  To make a call and terminate the persistent connection, set the CONNTYPE keyword to CLOSE.  
  
     If the call completes successfully, the returned COMTIContext array CONNTYPE keyword will have a value of NON-PERSISTENT.  
  
     Optionally, you can call ClosePersistentConnection at any time to close a persistent connection. The connection will be terminated and there will be no interaction with a server program.  
  
## Example  
 The following Visual Basic 6.0 code example shows how to use the OPEN and CLOSE method calls that might return an error. The sample also demonstrates how to determine whether a connection can still be used.  
  
```  
Public CtxCount As Long  
Public COMTIContext() As Variant  
Public ContextObj As COMTIContextLib.ContextObject  
  
Dim fConIsPersistent as Boolean  
Dim fConnIsViable as Boolean  
Dim varConnType as Variant  
  
Private Sub cmdBalance_Click()  
  On Error GoTo ErrorHandler  
  
OpenCall:  
  varConnType = "OPEN"  
  ContextObj.WriteContext "CONNTYPE", varConnType, COMTIContext  
  lngReturn = objBank.cedrbank(txtName.Text, txtAccount.Text, curRetBalance, COMTIContext)  
  
UseCall:  
  lngReturn = objBank.cedrbank(txtName.Text, txtAccount.Text, curRetBalance, COMTIContext)  
  
CloseCall:  
  If (fCloseWithMethod) Then  
      varConnType = "CLOSE"  
      ContextObj.WriteContext "CONNTYPE", varConnType, COMTIContext  
      lngReturn = objBank.cedrbank(txtName.Text, txtAccount.Text, curRetBalance, COMTIContext)  
  Else  
      COMTIContext = objBank.ClosePersistentConnection  
  End-if  
  
  Exit Sub  
  
ErrorHandler:  
    COMTIContext  = objBank.UpdateContextInfo   Optional for COM required for .NET  
    ContextObj.GetConnectionInfo (COMTIContext, fConnIsPersistent, fConnIsViable)  
    If (fConnIsPersistent = True And fConnIsViable = True) Then  
        Continue with the next Use or Close method call is OK  
    Else  
        Connection is either Non-persistent or no longer viable  
        So a Use or Close call is not valid  
    End-if  
    Exit Sub  
  
End Sub  
```  
  
## See Also  
 [Persistent Connections](../core/persistent-connections2.md)   
 [COMTIContext Interface](./comticontext-interface2.md)   
 [COMTIContext Keywords](./comticontext-keywords1.md)
