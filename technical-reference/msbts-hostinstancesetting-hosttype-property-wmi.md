---
title: MSBTS_HostInstanceSetting.HostType Property (WMI)
TOCTitle: MSBTS_HostInstanceSetting.HostType Property (WMI)
ms:assetid: 4d412cdc-458c-493a-a85e-31c6b1596034
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560054(v=BTS.80)
ms:contentKeyID: 51527908
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstanceSetting.HostType Property (WMI)

 

Indicates which runtime model the instances of the BizTalk Host will be running in.


> [!NOTE]
> <P>The syntax shown is language neutral.</P>



## Syntax

```C#
  
uint32 HostType;  
```

## Remarks

This property is read-only.

The following table contains the permissible values for this property:

<table>
<thead>
<tr class="header">
<th>Description</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>In-process</td>
<td>1</td>
</tr>
<tr class="even">
<td>Isolated</td>
<td>2</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

## Requirements

**Header**: Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace**: Included in \\root\\MicrosoftBizTalkServer.

