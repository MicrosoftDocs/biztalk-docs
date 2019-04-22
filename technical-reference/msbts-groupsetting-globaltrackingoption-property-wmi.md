---
title: MSBTS_GroupSetting.GlobalTrackingOption Property (WMI)
TOCTitle: MSBTS_GroupSetting.GlobalTrackingOption Property (WMI)
ms:assetid: 9f2bcaa2-346b-4e19-8a22-796d9994d40c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577636(v=BTS.80)
ms:contentKeyID: 51530032
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting.GlobalTrackingOption Property (WMI)

 

Gets the level of tracking that the BizTalk server should perform.

The syntax shown is language neutral.

## Syntax

```C#
  
uint32 GlobalTrackingOption;  
```

## Remarks

This property is read-write.

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
<td>Disable Tracking</td>
<td>0</td>
</tr>
<tr class="even">
<td>Normal Tracking</td>
<td>1</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

