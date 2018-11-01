---
title: MSBTS_HostInstance.HostType Property (WMI)
TOCTitle: MSBTS_HostInstance.HostType Property (WMI)
ms:assetid: bc7031d7-7c22-467a-a979-d7058227a2cb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578367(v=BTS.80)
ms:contentKeyID: 51530919
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstance.HostType Property (WMI)

 

Indicates which runtime model the instances of the BizTalk host will be running in. The syntax shown is language neutral.

## Syntax

``` 
  
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

