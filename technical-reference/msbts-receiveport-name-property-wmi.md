---
title: MSBTS_ReceivePort.Name Property (WMI)
TOCTitle: MSBTS_ReceivePort.Name Property (WMI)
ms:assetid: b7686057-0255-49a6-bc26-fdebf4a7d501
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578275(v=BTS.80)
ms:contentKeyID: 51530754
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
---

# MSBTS\_ReceivePort.Name Property (WMI)

 

Contains the name of the receive port.

*The syntax shown is language neutral.*

## Syntax

``` 
string Name;  
```

## Remarks

This property is required for instance creation. This property is writeable only at instance creation. After instance creation, this property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 256 characters.

This property wraps the managed **Microsoft.BizTalk.ExplorerOM.ReceivePort.Name** property.

## Example

The following example was taken from the SDK\\Samples\\Admin\\WMI\\Remove Receive Port\\VBScript\\RemoveReceivePort.vbs file.

``` vb
  
Sub RemoveReceivePort()  
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
   Dim strReceivePortName  
  
   strReceivePortName = objArgs(0)  
  
   'set up a WMI query to acquire a list of receive locations with the given Name and   
   'ReceivePortName key values.  This should be a list of zero or one Receive Locations.  
   strQuery = "SELECT * FROM MSBTS_ReceivePort WHERE Name =""" & strReceivePortName & """"  
   Set objInstSet = GetObject("Winmgmts:!root\MicrosoftBizTalkServer").ExecQuery(strQuery)  
  
   'Check for error condition before continuing.  
   If Err <> 0   Then  
      PrintWMIErrorThenExit Err.Description, Err.Number  
   End If  
  
   'If Receive Location found, enable it, otherwise print error and end.  
   If objInstSet.Count > 0 then  
      For Each objInst in objInstSet  
         'Now remove the receive port  
         objInst.Delete_()  
         If Err <> 0   Then  
            PrintWMIErrorThenExit Err.Description, Err.Number  
         End If  
         WScript.Echo "The Receive Port was successfully removed."  
      Next  
   Else  
      WScript.Echo "No Receive Port was found matching that Name."  
   End If  
  
End Sub  
  
```

No example is provided for C\#.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

