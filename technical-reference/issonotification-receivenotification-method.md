---
title: ISSONotification.ReceiveNotification Method
TOCTitle: ISSONotification.ReceiveNotification Method
ms:assetid: 3de270b8-6548-4c4b-9da7-de2043d77f98
ms:mtpsurl: https://msdn.microsoft.com/library/Aa770717(v=BTS.80)
ms:contentKeyID: 51527527
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
---

# ISSONotification.ReceiveNotification Method

 

Receives a notification from the ENTSSO system, such as password changes.

## Syntax

``` c++
  
HRESULT ReceiveNotification(  
ULONG ulNotificationFlagsIn,  
SReceiveNotification* pReceiveNotification,  
GUID* pguidTrackingId  
);  
```

#### Parameters

`bstrAdapterName`  
\[in\] The unique adapter name.

`ulNotificationFlagsIn`  
\[in\] The notification flags to control this notification, from the SSO\_NOTIFICATION\_FLAG enumeration.

`pReceiveNotification`  
\[in\] Pointer for the received notification.

`pguidTrackingId`  
\[out\] The tracking ID. The ENTSSO system will generate a tracking ID and return it to the caller. The tracking ID is used for auditing purposes and can also be used by the adapter to correlate responses to requests. This parameter can be NULL if the tracking ID is not required by the adapter.

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
<td>The method was successful.</td>
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
<td>ENTSSO_E_NO_NOTIFICATIONS</td>
<td>There are no notifications to be received.</td>
</tr>
<tr class="odd">
<td>ENTSSO_E_WRONG_STATE</td>
<td>This method has been called in the wrong state.</td>
</tr>
</tbody>
</table>


## Remarks

You can use **ReceiveNotification** to receive both password changes and other notifications from the ENTSSO system.

You may call **ReceiveNotification** with or without a WAIT flag. If you specify the WAIT flag, **ReceiveNotification** blocks until a notification is available. Doing so enables you to determine if you want to dedicate a thread for receiving notifications from the ENTSSO service, or whether you want to use the event handle returned from **InitializeAdapter** to perform your own waits, shared with other events.

If **ReceiveNotification** is waiting when you call [ShutdownAdapter](issonotification-shutdownadapter-method.md), then **ReceiveNotification** returns a SHUTDOWN notification as the last notification. The SHUTDOWN notification preempts any other pending notifications.

It is possible that multiple threads could be calling **ReceiveNotification** for the same adapter name. In this case, the request is single-threaded at the ENTSSO service, and only one **ReceiveNotification** completes with valid information. The threads complete with either the next notification or NONE. The reason is that each of these threads waits for the same event.

## Requirements

**Platforms:**  Windows

## See Also

[ISSONotification Interface (COM)](issonotification-interface-com.md)  
[ISSONotification Members](issonotification-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

