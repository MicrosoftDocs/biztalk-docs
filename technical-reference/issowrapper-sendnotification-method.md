---
description: "Learn more about: ISSOWrapper.SendNotification Method"
title: ISSOWrapper.SendNotification Method
TOCTitle: ISSOWrapper.SendNotification Method
ms:assetid: ac203b80-31eb-4dcf-9bc3-3f8221566502
ms:mtpsurl: https://msdn.microsoft.com/library/Aa705152(v=BTS.80)
ms:contentKeyID: 51530402
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
dev_langs:
- c++
---

# ISSOWrapper.SendNotification Method

 

Sends a notification from the adapter to the ENTSSO service.

## Syntax

``` c++
  
HRESULT SendNotification(  
ULONG ulNotificationType,   
ULONG ulNotificationFlags,   
Guid guidTrackingIdIn,   
bstr bstrExternalAccount,   
bstr bstrNewExternalPassword,   
bstr bstrOldExternalPassword,   
ulonglong ullTimestamp,   
ulonglong ullErrorCode,   
bstr bstrErrorMessage,   
out Guid *pguidTrackingIdOut  
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
<td><code>ulNotificationType</code></td>
<td>Notification type.</td>
</tr>
<tr class="even">
<td><code>ulNotificationFlags</code></td>
<td>Notification flags.</td>
</tr>
<tr class="odd">
<td><code>guidTrackingIdIn</code></td>
<td>The tracking id of the password change to be confirmed.</td>
</tr>
<tr class="even">
<td><code>bstrExternalAccount</code></td>
<td>The external account for which the password has changed.</td>
</tr>
<tr class="odd">
<td><code>bstrNewExternalPassword</code></td>
<td>The new password for the external account.</td>
</tr>
<tr class="even">
<td><code>bstrOldExternalPassword</code></td>
<td>Optional. The old password for the external account.</td>
</tr>
<tr class="odd">
<td><code>ullTimestamp</code></td>
<td>The timestamp when the password change was made, or zero to use the current time.</td>
</tr>
<tr class="even">
<td><code>ullErrorCode</code></td>
<td>If non-zero, the external password change failed. errorCode will be written to the event log. Zero for successful external password changes.</td>
</tr>
<tr class="odd">
<td><code>bstrErrorMessage</code></td>
<td>Optional. The message to write to the event log if the password change failed.</td>
</tr>
<tr class="even">
<td><code>pguidTrackingIdOut</code></td>
<td>Optional. On return, contains a pointer to a GUID to receive the tracking id.</td>
</tr>
</tbody>
</table>


## Property Value/Return Value

E\_ACCESS\_DENIED  
Access is denied.

## Exceptions

## Remarks

SendNotification uses different parameters depending on the notificationType. The following table describes the necessary parameters for each type of notification.

<table>
<thead>
<tr class="header">
<th>notificationType</th>
<th>Parameters</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>SSO_NOTIFICATION_TYPE_PASSWORD_CHANGE</td>
<td>externalAccount<br />
<br />
newExternalPassword<br />
<br />
oldExternalPassword<br />
<br />
timestamp</td>
</tr>
<tr class="even">
<td>SSO_NOTIFICATION_TYPE_PASSWORD_CHANGE_COMPLETE</td>
<td>trackingIdIn<br />
<br />
errorCode<br />
<br />
errorMessage</td>
</tr>
<tr class="odd">
<td>SSO_NOTIFICATION_TYPE_STATUS_OFFLINE</td>
<td>errorCode<br />
<br />
errorMessage</td>
</tr>
<tr class="even">
<td>SSO_NOTIFICATION_TYPE_PASSWORD_EXPIRED</td>
<td>externalAccount</td>
</tr>
<tr class="odd">
<td>SSO_NOTIFICATION_TYPE_STATUS_REQUEST</td>
<td>None</td>
</tr>
<tr class="even">
<td>SSO_NOTIFICATION_TYPE_STATUS_ONLINE</td>
<td>None</td>
</tr>
</tbody>
</table>


## Requirements

