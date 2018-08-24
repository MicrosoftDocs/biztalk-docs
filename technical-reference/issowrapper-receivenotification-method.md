---
title: ISSOWrapper.ReceiveNotification Method
TOCTitle: ISSOWrapper.ReceiveNotification Method
ms:assetid: e21e9fba-7114-49ff-a127-cac04991c8ef
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa705432(v=BTS.80)
ms:contentKeyID: 51532945
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
---

# ISSOWrapper.ReceiveNotification Method

 

Receives a notification to the adapter from the ENTSSO service.

## Syntax

``` c++
  
void ReceiveNotification(  
ULONG ulNotificationFlagsIn,  
GUID guidTrackingIdIn,  
out ULONG *pulNotificationType,  
out ULONG *pulNotificationFlagsOut,  
out BSTR *pbstrExternalAccount,  
out BSTR *pbstrNewExternalPassword,  
out BSTR *pbstrOldExternalPassword,  
out ULONGLONG *pullTimestamp,  
out ULONGLONG *pullErrorCode,  
out BSTR *pbstrErrorMessage,  
out SAFEARRAY(BSTR) *ppsaAdapters,  
out BSTR *pbstrAdapterName,  
out GUID *pguidTrackingIdOut  
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
<td><code>ulNotificationFlagsIn</code></td>
<td>The notification flags. Specify SSO_NOTIFICATION_FLAG_WAIT if you want your call to block waiting for a notification, or SSO_NOTIFICATION_FLAG_NONE.</td>
</tr>
<tr class="even">
<td><code>guidTrackingIdIn</code></td>
<td>The tracking ID.</td>
</tr>
<tr class="odd">
<td><code>pulNnotificationType</code></td>
<td>On return, contains a pointer to a ULONG that will receive the notification type.</td>
</tr>
<tr class="even">
<td><code>pulNotificationFlagsOut</code></td>
<td>On return, contains a pointer to a ULONG that will receive the notification flags</td>
</tr>
<tr class="odd">
<td><code>pbstrExternalAccount</code></td>
<td>On return, contains the external account for which the password should be changed.</td>
</tr>
<tr class="even">
<td><code>newExternalPassword</code></td>
<td>On return, contains the new password for the external account.</td>
</tr>
<tr class="odd">
<td><code>pbstrOldExternalPassword</code></td>
<td>Optional. On return, contains the old password for the external account.</td>
</tr>
<tr class="even">
<td><code>pullTimestamp</code></td>
<td>On return, contains the timestamp when the password change was made.</td>
</tr>
<tr class="odd">
<td><code>pullErrorCode</code></td>
<td>On return, contains the error code.</td>
</tr>
<tr class="even">
<td><code>pbstrErrorMessage</code></td>
<td>On return, contains an error message.</td>
</tr>
<tr class="odd">
<td><code>ppsaAdapters</code></td>
<td>On return, contains an array of adapter names.</td>
</tr>
<tr class="even">
<td><code>pbstrAdapterName</code></td>
<td>On return, contains the adapter name.</td>
</tr>
<tr class="odd">
<td><code>pbuidTrackingIdOut</code></td>
<td>On return, contains the tracking ID.</td>
</tr>
</tbody>
</table>


## Return Value

This method returns an HRESULT indicating whether it completed correctly. For more information, see the Exceptions section.

## Exceptions

E\_ACCESS\_DENIED  
Access is denied.

## Remarks

ReceiveNotification uses different parameters to return information depending on the notificationType. The following table describes the relationship between the different parameters and types of notifications.

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

