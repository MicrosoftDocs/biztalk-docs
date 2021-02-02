---
description: "Learn more about: MSBTS_ReceiveLocation.IsDisabled Property (WMI)"
title: MSBTS_ReceiveLocation.IsDisabled Property (WMI)
TOCTitle: MSBTS_ReceiveLocation.IsDisabled Property (WMI)
ms:assetid: f9de515d-285f-434c-b2f1-23e5f26148f1
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562046(v=BTS.80)
ms:contentKeyID: 51533553
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
---

# MSBTS\_ReceiveLocation.IsDisabled Property (WMI)

 

Enables or disables a receive function.

*The syntax shown is language neutral.*

## Syntax

```C#
  
boolean IsDisabled = true;  
```

## Remarks

This property is read-only.

The default value for this property is **true**.

## Example

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

