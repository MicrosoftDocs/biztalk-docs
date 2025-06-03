---
description: "Learn more about: MSBTS_HostInstance.ConfigurationState Property (WMI)"
title: MSBTS_HostInstance.ConfigurationState Property (WMI)
TOCTitle: MSBTS_HostInstance.ConfigurationState Property (WMI)
ms:assetid: 63ba5883-31c2-4604-8e90-e69cd9418d63
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560498(v=BTS.80)
ms:contentKeyID: 51528526
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_HostInstance.ConfigurationState Property (WMI)

 

Contains the installation state for given instance of the BizTalk host.

## Property Declaration

*The syntax shown is language neutral.*

```C#
uint32 ConfigurationState;  
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
<td>Installed</td>
<td>1</td>
</tr>
<tr class="even">
<td>Installation failed</td>
<td>2</td>
</tr>
<tr class="odd">
<td>Uninstallation failed</td>
<td>3</td>
</tr>
<tr class="even">
<td>Update failed</td>
<td>4</td>
</tr>
<tr class="odd">
<td>Not installed</td>
<td>5</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

For samples illustrating the **MSBTS\_HostInstance** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

