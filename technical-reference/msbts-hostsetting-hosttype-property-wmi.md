---
description: "Learn more about: MSBTS_HostSetting.HostType Property (WMI)"
title: MSBTS_HostSetting.HostType Property (WMI)
TOCTitle: MSBTS_HostSetting.HostType Property (WMI)
ms:assetid: cc80179e-3f3f-4622-bc7d-2926e5a8bff1
ms:mtpsurl: https://msdn.microsoft.com/library/Aa548043(v=BTS.80)
ms:contentKeyID: 51531375
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostSetting.HostType Property (WMI)

 

Indicates which runtime model the instances of the BizTalk Host will be running in.


> [!NOTE]
> <P>The syntax shown is language neutral.</P>



## Syntax

```C#
  
uint32 HostType;  
```

## Remarks

This property is read only.

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

For samples illustrating the **MSBTS\_HostInstance** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

