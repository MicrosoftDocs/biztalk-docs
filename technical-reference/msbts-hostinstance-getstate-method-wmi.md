---
description: "Learn more about: MSBTS_HostInstance.GetState Method (WMI)"
title: MSBTS_HostInstance.GetState Method (WMI)
TOCTitle: MSBTS_HostInstance.GetState Method (WMI)
ms:assetid: bc8502b8-50db-47fe-b403-57a258be45f5
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578369(v=BTS.80)
ms:contentKeyID: 51530868
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstance.GetState Method (WMI)

 

Retrieves the state of the given instance of the BizTalk host.

## Method Declaration

*The syntax shown is language neutral.*

```C#
uint32 GetState(   
          [out] uint32 State  
);  
```

## Parameters

*State*

\[out\] **Integer** describing the state of the BizTalk host instance.

## Remarks

The following table contains the possible values for the *State* parameter:

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

