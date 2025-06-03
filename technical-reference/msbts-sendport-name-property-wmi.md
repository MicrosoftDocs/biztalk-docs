---
description: "Learn more about: MSBTS_SendPort.Name Property (WMI)"
title: MSBTS_SendPort.Name Property (WMI)
TOCTitle: MSBTS_SendPort.Name Property (WMI)
ms:assetid: 6bb286c9-7385-4c5c-ba30-f22f9092e01d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560659(v=BTS.80)
ms:contentKeyID: 51528744
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
ms.topic: reference
---

# MSBTS\_SendPort.Name Property (WMI)

 

Contains the name of the send port.

*The syntax shown is language neutral.*

## Syntax

```C#
string Name;  
```

## Remarks

This property is required for instance creation. This property is only writeable at instance creation. After instance creation, this property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 256 characters.

This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPort.Name** property.

## Example

The following example was taken from the SDK\\Samples\\Admin\\WMI\\Remove Send Port\\VBScript\\RemoveSendPort.vbs file.

``` vb
  
Sub RemoveSendPort()  
   'Get the command line arguments entered for the script  
   Dim objArgs: Set objArgs = WScript.Arguments  
  
   'error handling is done by explicity checking the err object rather than using  
   'the VB ON ERROR construct, so set to resume next on error.  
   On Error Resume Next  
  
   'Make sure the expected number of arguments were provided on the command line.  
   'if not, print usage text and exit.  
   If (objArgs.Count <> 1) Then  
      PrintUsage()  
      WScript.Quit 0  
   End If  
  
   Dim objInstSet, objInst, strQuery  
   Dim strSendPortName  
  
   strSendPortName = objArgs(0)  
  
   'set up a WMI query to acquire a list of send ports with the given Name key value.  
   'This should be a list of zero or one Send Ports.  
   strQuery = "SELECT * FROM MSBTS_SendPort WHERE  Name =""" & strSendPortName & """"  
   Set objInstSet = GetObject("Winmgmts:!root\MicrosoftBizTalkServer").ExecQuery(strQuery)  
  
   'Check for error condition before continuing.  
   If Err <> 0   Then  
      PrintWMIErrorThenExit Err.Description, Err.Number  
   End If  
  
   'If Send Port found, Start it, otherwise print error and end.  
   If objInstSet.Count > 0 then  
      For Each objInst in objInstSet  
         'The send port must be unelisted first.  
         objInst.UnEnlist()  
         If Err <> 0   Then  
            PrintWMIErrorThenExit Err.Description, Err.Number  
         End If  
         WScript.Echo "The Send Port was successfully unenlisted."  
  
         'Now remove the send port  
         objInst.Delete_()  
         If Err <> 0   Then  
            PrintWMIErrorThenExit Err.Description, Err.Number  
         End If  
         WScript.Echo "The Send Port was successfully removed."  
      Next  
   Else  
      WScript.Echo "No Send Port was found matching that Name."  
   End If  
  
End Sub   
  
'This subroutine deals with all errors using the WbemScripting object.  Error descriptions  
'are returned to the user by printing to the console.  
Sub   PrintWMIErrorThenExit(strErrDesc, nErrNum)  
   On Error Resume   Next  
   Dim   objWMIError   : Set objWMIError =   CreateObject("WbemScripting.SwbemLastError")  
  
   If ( TypeName(objWMIError) = "Empty" ) Then  
      WScript.Echo strErrDesc & " (HRESULT: "   & Hex(nErrNum) & ")."  
   Else  
      WScript.Echo objWMIError.Description & "(HRESULT: "   & Hex(nErrNum) & ")."  
      Set objWMIError   = Nothing  
   End   If  
  
   'bail out  
   WScript.Quit 0  
End Sub  
  
```

The following example was taken from the SDK\\Samples\\Admin\\WMI\\Start Send Port\\VBScript\\StartSendPort.vbs file.

``` vb
  
Sub StartSendPort()  
   'Get the command line arguments entered for the script  
   Dim objArgs: Set objArgs = WScript.Arguments  
  
   'error handling is done by explicity checking the err object rather than using  
   'the VB ON ERROR construct, so set to resume next on error.  
   On Error Resume Next  
  
   'Make sure the expected number of arguments were provided on the command line.  
   'if not, print usage text and exit.  
   If (objArgs.Count < 1) Or (objArgs.Count > 2) Then  
      PrintUsage()  
      WScript.Quit 0  
   End If  
  
   Dim objInstSet, objInst, strQuery  
   Dim strSendPortName, strPrimaryTransportAddress  
  
   strSendPortName = objArgs(0)  
  
   'Check if PTAddress is to be set  
   If (objArgs.Count = 2) Then  
      'PTAddress for these samples are being set reletive to install location  
      ' NOTE: This is assuming that this is a FILE transport type  
      ' and we want to update it with the current directory  
      Dim WshShell  
      Set WshShell = WScript.CreateObject("WScript.Shell")  
  
      'Check for error condition before continuing.  
      If Err <> 0   Then  
         PrintWMIErrorThenExit Err.Description, Err.Number  
      End If  
  
      strPrimaryTransportAddress = WshShell.CurrentDirectory & objArgs(1)  
   Else  
      strPrimaryTransportAddress = ""  
   End If  
  
   'set up a WMI query to acquire a list of send ports with the given Name key value.  
   'This should be a list of zero or one Send Ports.  
   strQuery = "SELECT * FROM MSBTS_SendPort WHERE  Name =""" & strSendPortName & """"  
   Set objInstSet = GetObject("Winmgmts:!root\MicrosoftBizTalkServer").ExecQuery(strQuery)  
  
   'Check for error condition before continuing.  
   If Err <> 0   Then  
      PrintWMIErrorThenExit Err.Description, Err.Number  
   End If  
  
   'If Send Port found, Start it, otherwise print error and end.  
   If objInstSet.Count > 0 then  
      For Each objInst in objInstSet  
         'If the PTAddress is to be set, change it now  
         If "" <> strPrimaryTransportAddress Then  
            objInst.PTAddress = strPrimaryTransportAddress  
            If Err <> 0   Then  
               PrintWMIErrorThenExit Err.Description, Err.Number  
            End If  
            WScript.Echo "Primary Transport Address was set to:"  
            WScript.Echo strPrimaryTransportAddress  
         End If  
  
         'Now commit the change  
         objInst.Put_(1)  
         If Err <> 0   Then  
            PrintWMIErrorThenExit Err.Description, Err.Number  
         End If  
         WScript.Echo "Changes were successfully committed."  
  
         'Now start the send port  
         objInst.Start  
         If Err <> 0   Then  
            PrintWMIErrorThenExit Err.Description, Err.Number  
         End If  
         WScript.Echo "The Send Port was successfully started."  
      Next  
   Else  
      WScript.Echo "No Send Port was found matching that Name."  
   End If  
  
End Sub  
  
```

No sample is provided for C\#.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

