---
title: SSO_NOTIFICATION_TYPE Enumeration (COM)
TOCTitle: SSO_NOTIFICATION_TYPE Enumeration (COM)
ms:assetid: d97a99e2-059a-4574-8962-a7797cf5e7dd
ms:mtpsurl: https://msdn.microsoft.com/library/Aa772068(v=BTS.80)
ms:contentKeyID: 51531649
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
- csharp
- c++
- jscript
---

# SSO\_NOTIFICATION\_TYPE Enumeration (COM)

 

Specifies the different notification types used for Enterprise Single Sign-On (SSO).

## Syntax

``` vb
  
<Serializable>  
Public Enum SSO_NOTIFICATION_FLAG  
```

``` csharp
  
[Serializable]  
public enum SSO_NOTIFICATION_FLAG  
```

``` c++
  
[Serializable]  
__value public enum SSO_NOTIFICATION_FLAG  
```

``` jscript
  
            public   
   Serializable  
enum SSO_NOTIFICATION_FLAG  
```

## Members

<table>
<thead>
<tr class="header">
<th>Member Name</th>
<th>Value</th>
<th>Direction</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>SSO_NOTIFICATION_TYPE_NONE</strong></td>
<td>0x00000000</td>
<td>ENTSSO to adapter</td>
<td>No notifications are pending. This notification type is supported by group adapters. It is not necessary to confirm this notification.</td>
</tr>
<tr class="even">
<td><strong>SSO_NOTIFICATION_TYPE_SHUTDOWN</strong></td>
<td>0x00000001</td>
<td>ENTSSO to adapter</td>
<td>The ENTSSO service requires the adapter to shutdown. The adapter should respond by calling <a href="issonotification-shutdownadapter-method.md">ISSONotification.ShutdownAdapter Method</a>.<br />
<br />
This notification type is supported by group adapters. It indicates that the group adapter only should shut down. Each individual adapter that is part of the adapter group gets its own SHUTDOWN notification.<br />
<br />
It is not necessary to confirm this notification.</td>
</tr>
<tr class="odd">
<td><strong>SSO_NOTIFICATION_TYPE_SHUTDOWN_COMPLETE</strong></td>
<td>0x00000002</td>
<td>ENTSSO to adapter</td>
<td>The ENTSSO service has processed the <strong>ShutdownAdapter</strong> method. This is the last notification that is received by the adapter using the current event handle.<br />
<br />
This notification type is supported by group adapters.<br />
<br />
It is not necessary to confirm this notification.</td>
</tr>
<tr class="even">
<td><strong>SSO_NOTIFICATION_TYPE_PASSWORD_CHANGE</strong></td>
<td>0x00000003</td>
<td>Both</td>
<td>A password has changed.<br />
<br />
When sending a password change from an adapter to ENTSSO, the password change is considered to be accepted, and durable, on return from the notification to ENTSSO through <a href="issonotification-sendnotification-method.md">SendNotification</a>. That does not indicate that the password change is complete, but rather that it has been accepted, is durable, and is likely to be accomplished. Under some error conditions queues could fill up, in which case older password changes could be discarded. In general, you should perform more recent password changes than older ones.<br />
<br />
An adapter should make password changes received through <a href="issonotification-receivenotification-method.md">ReceiveNotification</a>, The adapter should make that change durable or effect the change immediately. The adapter should then call <strong>SendNotification</strong> with PASSWORD_CHANGE_COMPLETE for that password change to delete it from the database queue.<br />
<br />
This notification type is not supported by group adapters.<br />
<br />
An adapter must confirm this notification. It is optional for ENTSSO to confirm this notification.</td>
</tr>
<tr class="odd">
<td><strong>SSO_NOTIFICATION_TYPE_PASSWORD_CHANGE_COMPLETE</strong></td>
<td>0x00000004</td>
<td>Both</td>
<td>The ENTSSO service completed the password change. Note that the definition of complete may vary depending on what is configured. For more information, see the Remarks section of <a href="issonotification-receivenotification-method.md">ReceiveNotification</a>.<br />
<br />
You can use the tracking ID to correlate the original request with the response.<br />
<br />
This notification type is not supported by group adapters.<br />
<br />
It is not necessary to confirm this notification.</td>
</tr>
<tr class="even">
<td><strong>SSO_NOTIFICATION_TYPE_PASSWORD_EXPIRED</strong></td>
<td>0x00000005</td>
<td>Both</td>
<td>The password for an account has expired. For ENTSSO, this causes the stored password for this account to be flagged as <strong>expired</strong>.<br />
<br />
This notification type is not supported by group adapters.<br />
<br />
It is necessary for an adapter to confirm this notification. It is optional for ENTSSO to confirm this notification.<br />
<br />
Note that this notification is currently not implemented. ENTSSO will ignore any SSO_NOTIFICATION_TYPE_PASSWORD_EXPIRE messages, and will never send a message of this type to an adapter.</td>
</tr>
<tr class="odd">
<td><strong>SSO_NOTIFICATION_TYPE_STATUS_REQUEST</strong></td>
<td>0x00000006</td>
<td>Both</td>
<td>An inquiry regarding the status of the adapter or ENTSSO service, or as a response.<br />
<br />
If the ENTSSO service detects that a password sync adapter has not sent any password changes for some time, it may send a STATUS notification to that adapter as a &quot;keep alive&quot;. The adapter should respond with a STATUS_ONLINE or STATUS_OFFLINE notification.<br />
<br />
This notification type is supported by group adapters. It applies only for the status of the group adapter, not for the adapters within the adapter group.<br />
<br />
It is not necessary to confirm this notification.</td>
</tr>
<tr class="even">
<td><strong>SSO_NOTIFICATION_TYPE_STATUS_ONLINE</strong></td>
<td>0x00000007</td>
<td>Both</td>
<td>The status of an adapter or ENTSSO service is online.<br />
<br />
If the ENTSSO service detects that a password sync adapter has not sent any password changes for some time, it may send a STATUS notification to that adapter as a &quot;keep alive&quot;. If online, the adapter should respond with a STATUS_ONLINE.<br />
<br />
If the adapter detects that it is offline, it can send these notifications unsolicited.<br />
<br />
This notification type is supported by group adapters. It applies only for the status of the group adapter, not for the adapters within the adapter group.<br />
<br />
It is not necessary to confirm this notification.</td>
</tr>
<tr class="odd">
<td><strong>SSO_NOTIFICATION_TYPE_STATUS_OFFLINE</strong></td>
<td>0x00000008</td>
<td>Both</td>
<td>The adapter or ENTSSO service is offline.<br />
<br />
If the ENTSSO service detects that a password sync adapter has not sent any password changes for some time, it may send a STATUS notification to that adapter as a &quot;keep alive&quot;. If your adapter is offline, it should respond with a STATUS_OFFLINE notification.<br />
<br />
If the adapter detects that it is offline, it can send these notifications unsolicited.<br />
<br />
This notification type is supported by group adapters. It applies only for the status of the group adapter, not for the adapters within the adapter group.<br />
<br />
It is not necessary to confirm this notification.</td>
</tr>
<tr class="even">
<td><strong>SSO_NOTIFICATION_TYPE_ADAPTERS_IN_GROUP</strong></td>
<td>0x00001000</td>
<td>ENTSSO to adapter</td>
<td>An adapter is contained within a specified adapter group. It is one of the first notifications received by a group adapter after initialization.<br />
<br />
The adapter names are contained within the &quot;new external credentials array&quot; parameter. If there are a very large number of adapters in this adapter group, it is possible that this notification is received by the group adapter more than once with the remaining adapter names.<br />
<br />
This notification type is only issued to group adapters. It is not necessary to confirm this notification.</td>
</tr>
<tr class="odd">
<td><strong>SSO_NOTIFICATION_TYPE_ADD_ADAPTER</strong></td>
<td>0x00001001</td>
<td>ENTSSO to adapter</td>
<td>An adapter has been added to the adapter group.<br />
<br />
The adapter name that has been added is contained within the &quot;notification string&quot; parameter.<br />
<br />
This notification type is only issued to group adapters. It is not necessary to confirm this notification.</td>
</tr>
<tr class="even">
<td><strong>SSO_NOTIFICATION_TYPE_DELETE_ADAPTER</strong></td>
<td>0x00001002</td>
<td>ENTSSO to adapter</td>
<td>An adapter has been deleted from the adapter group.<br />
<br />
The adapter name that has been deleted is contained within the &quot;notification string&quot; parameter.<br />
<br />
This notification type is only issued to group adapters. It is not necessary to confirm this notification.</td>
</tr>
</tbody>
</table>


## Remarks

There is no online or offline notification for adapters to the group adapter. This is because control of the individual adapters is handled by each adapter itself.

In general, the notifications that require confirmation are those that are durable in the database queue. The other notifications are control and status information which are transient. Notifications that require confirmation have one of the confirm flags set.

There is no notification to or from the adapter about enabled or disabled status. This is because the enable and disable is handled by the enable and disable of the underlying configuration store application. Thus, when the adapter is disabled by an administrator, the adapter receives access denied messages from all calls to ENTSSO.

## Requirements

**Type Library:** SSOLookup 1.0 Type Library (SSOLookup.dll)

**Platforms:**  Windows

## See Also

[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

