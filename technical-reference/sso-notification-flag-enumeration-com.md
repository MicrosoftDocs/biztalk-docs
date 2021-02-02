---
description: "Learn more about: SSO_NOTIFICATION_FLAG Enumeration (COM)"
title: SSO_NOTIFICATION_FLAG Enumeration (COM)
TOCTitle: SSO_NOTIFICATION_FLAG Enumeration (COM)
ms:assetid: 616829c9-25cd-4c5c-8f4e-47edcfe2bfc7
ms:mtpsurl: https://msdn.microsoft.com/library/Aa771088(v=BTS.80)
ms:contentKeyID: 51528448
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
- csharp
- c++
- jscript
---

# SSO\_NOTIFICATION\_FLAG Enumeration (COM)

 

Specifies the different types of flags used for Enterprise Single Sign-On (SSO).

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

## Remarks

The following table describes the possible values for the notification flags.

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
<td><strong>SSO_NOTIFICATION_FLAG_NONE</strong></td>
<td>0x00000000</td>
<td>Both</td>
<td>Null value.</td>
</tr>
<tr class="even">
<td><strong>SSO_NOTIFICATION_FLAG_ADMIN_CHANGE</strong></td>
<td>0x00000001</td>
<td>Both</td>
<td>The password change was a result of an administrator action. Some systems will be able to distinguish between an administrator action, while some will not. ENTSSO will not set this flag.<br />
<br />
This flag is currently not used.</td>
</tr>
<tr class="odd">
<td><strong>SSO_NOTIFICATION_FLAG_TEST</strong></td>
<td>0x00000008</td>
<td>Both</td>
<td>The current notification is a test request.<br />
<br />
Your adapter can safely ignore this notification. You can use this notification for testing and diagnostics purposes.<br />
<br />
This flag is currently not used.</td>
</tr>
<tr class="even">
<td><strong>SSO_NOTIFICATION_FLAG_AUDIT</strong></td>
<td>0x00000010</td>
<td>Both</td>
<td>The current request requires auditing.<br />
<br />
This flag is currently not used.</td>
</tr>
<tr class="odd">
<td><strong>SSO_NOTIFICATION_FLAG_WINDOWS</strong></td>
<td>0x00000020</td>
<td>Not applicable</td>
<td>Reserved for internal use.</td>
</tr>
<tr class="even">
<td><strong>SSO_NOTIFICATION_FLAG_WAIT</strong></td>
<td>0x00000040</td>
<td>Adapter to ENTSSO</td>
<td><strong>ReceiveNotification</strong> should block and wait until a notification is available.<br />
<br />
Best practice indicates you should set this flag and allow the PS Helper to wait for notifications.</td>
</tr>
<tr class="odd">
<td><strong>SSO_NOTIFICATION_FLAG_SEND_ONLY</strong></td>
<td>0x00000080</td>
<td>Adapter to ENTSSO</td>
<td>Indicates that this PS Helper should initialize for sending only. It assumes that another PS Helper will be initialized normally.<br />
<br />
You should use this flag when using one PS Helper for ReceiveNotification (for receiving password changes), and another fro SendNotification (for sending password changes).</td>
</tr>
</tbody>
</table>


## Requirements

**Type Library:** SSOPSHelper 1.0 Type Library (SSOPSHelper.dll)

**Platforms:**  Windows

## See Also

[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

