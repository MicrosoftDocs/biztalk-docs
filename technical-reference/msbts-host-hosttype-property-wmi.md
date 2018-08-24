---
title: MSBTS_Host.HostType Property (WMI)
TOCTitle: MSBTS_Host.HostType Property (WMI)
ms:assetid: 9dbeaabf-6a43-4b87-8f1e-cdf72481a418
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577590(v=BTS.80)
ms:contentKeyID: 51530035
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Host.HostType Property (WMI)

 

Indicates which runtime model the instances of the BizTalk Host will be running in. The syntax shown is language neutral.

## Syntax

``` 
  
unint32 HostType;  
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


In-process hosts represent service instances that an administrator creates, deletes, and fully controls with WMI and the BizTalk Administration console.

Isolated hosts represent service instances that a solutions developer programmatically creates, deletes, and controls. An administrator uses WMI and the BizTalk Administration console to configure these hosts (for example, to configure the host service account and authentication trust).

For more information about in-process and isolated hosts, see [Hosts](https://msdn.microsoft.com/en-us/library/aa578695\(v=bts.80\)).

Note that the integer values must be used in code and script.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

