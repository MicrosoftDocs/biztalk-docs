---
title: MSBTS_ReceiveLocation.PipelineName Property (WMI)
TOCTitle: MSBTS_ReceiveLocation.PipelineName Property (WMI)
ms:assetid: 45637645-b64e-465f-bc06-3b6a8455cb0c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559859(v=BTS.80)
ms:contentKeyID: 51527714
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
---

# MSBTS\_ReceiveLocation.PipelineName Property (WMI)

 

Contains the name of the pipeline that will process the document before the document is submitted to the MessageBox database.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string PipelineName;  
```

## Remarks

This property is read-write.

This property is required for instance creation.

The maximum length for this property is 256 characters.

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

