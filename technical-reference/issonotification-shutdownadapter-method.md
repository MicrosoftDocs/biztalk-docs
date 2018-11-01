---
title: ISSONotification.ShutdownAdapter Method
TOCTitle: ISSONotification.ShutdownAdapter Method
ms:assetid: e1326ddc-476e-421c-a06e-fb8a557f2f09
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa705416(v=BTS.80)
ms:contentKeyID: 51532918
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
---

# ISSONotification.ShutdownAdapter Method

 

Indicates that the password sync adapter is shutting down.

## Syntax

``` c++
  
HRESULT ShutDownAdapter(  
GUID* pguidTrackingId   
);  
```

#### Parameters

`pguidTrackingId`  
\[out\] When this method returns, contains the tracking ID. The tracking ID is the same tracking ID that ENTSSO returns in the initialization process, which you can use for auditing purposes. May be NULL.

## Return Value

This method returns an HRESULT indicating whether it completed correctly. For more information, see the Error Values section.

## Error Values

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

**ShutdownAdapter** should be the last method you call. You may call neither [SendNotification](issonotification-sendnotification-method.md) nor [ReceiveNotification](issonotification-receivenotification-method.md) after you call **ShutdownAdapter.** The only method you may call afterward is [InitializeAdapter](issonotification-initializeadapter-method.md), which initializes a new session.

Calls to **SendNotification** or **ReceiveNotification** that are in progress (on other threads) when you call **ShutdownAdapter** may receive ENTSSO\_E\_WRONG\_STATE, although one thread calling **ReceiveNotification** receives the SHUTDOWN\_COMPLETE notification.

**ShutdownAdapter** is single-threaded. ENTSSO blocks all other threads calling **ShutdownAdapter** until **ShutdownAdapter** has completed. **ShutdownAdapter** is also synchronized with the **InitializeAdapter** method.

## Requirements

**Platforms:**  Windows

## See Also

[ISSONotification Interface (COM)](issonotification-interface-com.md)  
[ISSONotification Members](issonotification-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/en-us/library/aa704508\(v=bts.80\))

