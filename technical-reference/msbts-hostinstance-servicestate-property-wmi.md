---
title: MSBTS_HostInstance.ServiceState Property (WMI)
TOCTitle: MSBTS_HostInstance.ServiceState Property (WMI)
ms:assetid: 982db257-a2b7-4a39-994e-46d7cf333ea5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577472(v=BTS.80)
ms:contentKeyID: 51529904
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstance.ServiceState Property (WMI)

 

Contains the state of the host instance.

## Property Declaration

*The syntax shown is language neutral.*

```C#
uint32 ServiceState;  
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
<td>Stopped</td>
<td>1</td>
</tr>
<tr class="even">
<td>Start pending</td>
<td>2</td>
</tr>
<tr class="odd">
<td>Stop pending</td>
<td>3</td>
</tr>
<tr class="even">
<td>Running</td>
<td>4</td>
</tr>
<tr class="odd">
<td>Continue pending</td>
<td>5</td>
</tr>
<tr class="even">
<td>Pause pending</td>
<td>6</td>
</tr>
<tr class="odd">
<td>Paused</td>
<td>7</td>
</tr>
<tr class="even">
<td>Unknown</td>
<td>8</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

For samples illustrating the **MSBTS\_HostInstance** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

