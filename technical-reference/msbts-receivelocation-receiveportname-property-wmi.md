---
title: MSBTS_ReceiveLocation.ReceivePortName Property (WMI)
TOCTitle: MSBTS_ReceiveLocation.ReceivePortName Property (WMI)
ms:assetid: 74019597-cacd-424b-bf19-370c3c94d3ec
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560827(v=BTS.80)
ms:contentKeyID: 51528968
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
---

# MSBTS\_ReceiveLocation.ReceivePortName Property (WMI)

 

Contains the name of the receive port used by the receive location.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string ReceivePortName;  
```

## Remarks

This property is read-only.

This property is required for instance creation.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride, Name,** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 256 characters.

## Example

The following example was taken from the SDK\\Samples\\Admin\\WMI\\Enable Receive Location\\VBScript\\EnableRecLoc.vbs file.

``` vb
  
Sub EnableReceiveLocation()  
   'Get the command line arguments entered for the script  
   Dim objArgs: Set objArgs = WScript.Arguments  
  
   'error handling is done by explicity checking the err object rather than using  
   'the VB ON ERROR construct, so set to resume next on error.  
   On Error Resume Next  
  
   'Make sure the expected number of arguments were provided on the command line.  
   'if not, print usage text and exit.  
   If (objArgs.Count < 2) Or (objArgs.Count > 3) Then  
      PrintUsage()  
      WScript.Quit 0  
   End If  
  
   Dim objInstSet, objInst, strQuery  
   Dim strReceivePortName, strReceiveLocationName, strTransportURL  
  
   strReceivePortName = objArgs(0)  
   strReceiveLocationName = objArgs(1)  
  
   'Check if TransportURL is to be set  
   If (objArgs.Count = 3) Then  
      'TransportURI for these samples are being set reletive to install location  
      ' NOTE: This is assuming that this is a FILE transport type  
      ' and we want to update it with the current directory  
      Dim WshShell  
      Set WshShell = WScript.CreateObject("WScript.Shell")  
  
      'Check for error condition before continuing.  
      If Err <> 0   Then  
         PrintWMIErrorThenExit Err.Description, Err.Number  
      End If  
  
      strTransportURL = WshShell.CurrentDirectory & objArgs(2)  
   Else  
      strTransportURL = ""  
   End If  
  
   'set up a WMI query to acquire a list of receive locations with the given Name and   
   'ReceivePortName key values.  This should be a list of zero or one Receive Locations.  
   strQuery = "SELECT * FROM MSBTS_ReceiveLocation WHERE  ReceivePortName =""" & strReceivePortName & """AND Name =""" & strReceiveLocationName & """"  
   Set objInstSet = GetObject("Winmgmts:!root\MicrosoftBizTalkServer").ExecQuery(strQuery)  
  
   'Check for error condition before continuing.  
   If Err <> 0   Then  
      PrintWMIErrorThenExit Err.Description, Err.Number  
   End If  
  
   'If Receive Location found, enable it, otherwise print error and end.  
   If objInstSet.Count > 0 then  
      For Each objInst in objInstSet  
         'If the TransportURL is to be set, change it now  
         If "" <> strTransportURL Then  
            objInst.InboundTransportURL = strTransportURL  
            If Err <> 0   Then  
               PrintWMIErrorThenExit Err.Description, Err.Number  
            End If  
            WScript.Echo "Inbound Transport URL was set to:"  
            WScript.Echo strTransportURL  
         End If  
  
         'Now commit the change  
         objInst.Put_(1)  
         If Err <> 0   Then  
            PrintWMIErrorThenExit Err.Description, Err.Number  
         End If  
         WScript.Echo "Changes were successfully committed."  
  
         'Now enable to receive location  
         objInst.Enable  
         If Err <> 0   Then  
            PrintWMIErrorThenExit Err.Description, Err.Number  
         End If  
         WScript.Echo "The Receive Location was successfully enabled."  
      Next  
   Else  
      WScript.Echo "No Receive Location was found matching that Name."  
   End If  
  
End Sub  
  
```

The following example was taken from the SDK\\Samples\\Admin\\WMI\\Enumerate Receive Locations\\VBScript\\EnumRecLocs.vbs file.

``` vb
  
Sub EnumRecLocs()  
  
   'error handling is done by explicity checking the err object rather than using  
   'the VB ON ERROR construct, so set to resume next on error.  
   on error resume next  
  
   Dim InstSet, Inst  
   set InstSet = GetObject ("winmgmts:\root\MicrosoftBizTalkServer").InstancesOf("MSBTS_ReceiveLocation")  
  
   'Check for error condition before continuing.  
   If Err <> 0   Then  
      PrintWMIErrorThenExit Err.Description, Err.Number  
   End If  
  
   'Report on number of receive locations found and list each one.  
   wscript.echo "A Total of " & InstSet.Count & " Receive Locations were found."  
   If InstSet.Count > 0 Then  
      For Each Inst In InstSet  
         wscript.echo  
         wscript.echo "Receive Location Name: " & Inst.Name  
         wscript.echo "  Disabled           : " & Inst.IsDisabled  
         wscript.echo "  Pipeline Name      : " & Inst.PipelineName  
         wscript.echo "  Receive Port Name  : " & Inst.ReceivePortName  
         wscript.echo  
      next  
   End If   
  
End Sub  
  
```

No example is provided for C\#.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

