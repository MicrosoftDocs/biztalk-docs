---
title: ISSOWrapper.ShutdownAdapter Method
TOCTitle: ISSOWrapper.ShutdownAdapter Method
ms:assetid: 3af07290-5a92-4fd3-82f5-b37165928b2f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa770674(v=BTS.80)
ms:contentKeyID: 51527444
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
---

# ISSOWrapper.ShutdownAdapter Method

 

Indicates to the ENTSSO service that the adapter is shutting down.

## Syntax

``` c++
  
HRESULT ShutDownAdapter(  
GUID* pguidTrackingId  
);  
```

#### Parameters

<table>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><code>pguidtrackingId</code></td>
<td>When this method returns, contains the tracking ID. The tracking ID is the same tracking ID that ENTSSO returns in the initialization process, which you can use for auditing purposes. May be NULL.</td>
</tr>
</tbody>
</table>


## Return Value

This method returns an HRESULT indicating whether it completed correctly. For more information, see the Error Values section.

## Exceptions

This method returns an HRESULT containing one of the values in the following table.

<table>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>S_OK</td>
<td>The shutdown was successful.</td>
</tr>
<tr class="even">
<td>E_ACCESSDENIED</td>
<td>Access is denied.</td>
</tr>
<tr class="odd">
<td>ENTSSO_E_NO_SERVER</td>
<td>Could not contact the ENTSSO server. Check that the ENTSSO service is running.</td>
</tr>
<tr class="even">
<td>ENTSSO_E_WRONG_STATE</td>
<td>This method has been called in the wrong state.</td>
</tr>
</tbody>
</table>


## Remarks

