---
title: MSBTS_HostInstanceSetting.ConfigurationState Property (WMI)
TOCTitle: MSBTS_HostInstanceSetting.ConfigurationState Property (WMI)
ms:assetid: e8b0ab09-a8b4-43cb-9cc4-f56f5deafe48
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561686(v=BTS.80)
ms:contentKeyID: 51533094
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstanceSetting.ConfigurationState Property (WMI)

 

Contains the installation state for given instance of the BizTalk host.

## Property Declaration

*The syntax shown is language neutral.*

```C#
uint32 ConfigurationState;  
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

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

