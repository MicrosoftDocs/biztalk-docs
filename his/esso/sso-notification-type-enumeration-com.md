---
description: "Learn more about: SSO_NOTIFICATION_TYPE Enumeration (COM)"
title: "SSO_NOTIFICATION_TYPE Enumeration (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0de34815-36b9-4efb-88c9-5329e5fe4355
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# SSO_NOTIFICATION_TYPE Enumeration (COM)
Specifies the different notification types used for Enterprise Single Sign-On (SSO).  
  
## Syntax  
  
```vb  
  
<Serializable>  
Public Enum SSO_NOTIFICATION_FLAG  
```  
  
```csharp  
  
[Serializable]  
public enum SSO_NOTIFICATION_FLAG  
```  
  
```cpp  
  
[Serializable]  
__value public enum SSO_NOTIFICATION_FLAG  
```  
  
```js  
  
            public   
   Serializable  
enum SSO_NOTIFICATION_FLAG  
```  
  
## Members  
  
|Member Name|Value|Direction|Description|  
|-----------------|-----------|---------------|-----------------|  
|**SSO_NOTIFICATION_TYPE_NONE**|0x00000000|ENTSSO to adapter|No notifications are pending. This notification type is supported by group adapters. It is not necessary to confirm this notification.|  
|**SSO_NOTIFICATION_TYPE_SHUTDOWN**|0x00000001|ENTSSO to adapter|The ENTSSO service requires the adapter to shutdown. The adapter should respond by calling [ISSONotification.ShutdownAdapter Method](../esso/issonotification-shutdownadapter-method.md).<br /><br /> This notification type is supported by group adapters. It indicates that the group adapter only should shut down. Each individual adapter that is part of the adapter group gets its own SHUTDOWN notification.<br /><br /> It is not necessary to confirm this notification.|  
|**SSO_NOTIFICATION_TYPE_SHUTDOWN_COMPLETE**|0x00000002|ENTSSO to adapter|The ENTSSO service has processed the **ShutdownAdapter** method. This is the last notification that is received by the adapter using the current event handle.<br /><br /> This notification type is supported by group adapters.<br /><br /> It is not necessary to confirm this notification.|  
|**SSO_NOTIFICATION_TYPE_PASSWORD_CHANGE**|0x00000003|Both|A password has changed.<br /><br /> When sending a password change from an adapter to ENTSSO, the password change is considered to be accepted, and durable, on return from the notification to ENTSSO through [SendNotification](../esso/issonotification-sendnotification-method.md). That does not indicate that the password change is complete, but rather that it has been accepted, is durable, and is likely to be accomplished. Under some error conditions queues could fill up, in which case older password changes could be discarded. In general, you should perform more recent password changes than older ones.<br /><br /> An adapter should make password changes received through [ReceiveNotification](../esso/issonotification-receivenotification-method.md), The adapter should make that change durable or effect the change immediately. The adapter should then call **SendNotification** with PASSWORD_CHANGE_COMPLETE for that password change to delete it from the database queue.<br /><br /> This notification type is not supported by group adapters.<br /><br /> An adapter must confirm this notification. It is optional for ENTSSO to confirm this notification.|  
|**SSO_NOTIFICATION_TYPE_PASSWORD_CHANGE_COMPLETE**|0x00000004|Both|The ENTSSO service completed the password change. Note that the definition of complete may vary depending on what is configured. For more information, see the Remarks section of [ReceiveNotification](../esso/issonotification-receivenotification-method.md).<br /><br /> You can use the tracking ID to correlate the original request with the response.<br /><br /> This notification type is not supported by group adapters.<br /><br /> It is not necessary to confirm this notification.|  
|**SSO_NOTIFICATION_TYPE_PASSWORD_EXPIRED**|0x00000005|Both|The password for an account has expired. For ENTSSO, this causes the stored password for this account to be flagged as **expired**.<br /><br /> This notification type is not supported by group adapters.<br /><br /> It is necessary for an adapter to confirm this notification. It is optional for ENTSSO to confirm this notification.<br /><br /> Note that this notification is currently not implemented. ENTSSO will ignore any SSO_NOTIFICATION_TYPE_PASSWORD_EXPIRE messages, and will never send a message of this type to an adapter.|  
|**SSO_NOTIFICATION_TYPE_STATUS_REQUEST**|0x00000006|Both|An inquiry regarding the status of the adapter or ENTSSO service, or as a response.<br /><br /> If the ENTSSO service detects that a password sync adapter has not sent any password changes for some time, it may send a STATUS notification to that adapter as a "keep alive". The adapter should respond with a STATUS_ONLINE or STATUS_OFFLINE notification.<br /><br /> This notification type is supported by group adapters. It applies only for the status of the group adapter, not for the adapters within the adapter group.<br /><br /> It is not necessary to confirm this notification.|  
|**SSO_NOTIFICATION_TYPE_STATUS_ONLINE**|0x00000007|Both|The status of an adapter or ENTSSO service is online.<br /><br /> If the ENTSSO service detects that a password sync adapter has not sent any password changes for some time, it may send a STATUS notification to that adapter as a "keep alive". If online, the adapter should respond with a STATUS_ONLINE.<br /><br /> If the adapter detects that it is offline, it can send these notifications unsolicited.<br /><br /> This notification type is supported by group adapters. It applies only for the status of the group adapter, not for the adapters within the adapter group.<br /><br /> It is not necessary to confirm this notification.|  
|**SSO_NOTIFICATION_TYPE_STATUS_OFFLINE**|0x00000008|Both|The adapter or ENTSSO service is offline.<br /><br /> If the ENTSSO service detects that a password sync adapter has not sent any password changes for some time, it may send a STATUS notification to that adapter as a "keep alive". If your adapter is offline, it should respond with a STATUS_OFFLINE notification.<br /><br /> If the adapter detects that it is offline, it can send these notifications unsolicited.<br /><br /> This notification type is supported by group adapters. It applies only for the status of the group adapter, not for the adapters within the adapter group.<br /><br /> It is not necessary to confirm this notification.|  
|**SSO_NOTIFICATION_TYPE_ADAPTERS_IN_GROUP**|0x00001000|ENTSSO to adapter|An adapter is contained within a specified adapter group. It is one of the first notifications received by a group adapter after initialization.<br /><br /> The adapter names are contained within the "new external credentials array" parameter. If there are a very large number of adapters in this adapter group, it is possible that this notification is received by the group adapter more than once with the remaining adapter names.<br /><br /> This notification type is only issued to group adapters. It is not necessary to confirm this notification.|  
|**SSO_NOTIFICATION_TYPE_ADD_ADAPTER**|0x00001001|ENTSSO to adapter|An adapter has been added to the adapter group.<br /><br /> The adapter name that has been added is contained within the "notification string" parameter.<br /><br /> This notification type is only issued to group adapters. It is not necessary to confirm this notification.|  
|**SSO_NOTIFICATION_TYPE_DELETE_ADAPTER**|0x00001002|ENTSSO to adapter|An adapter has been deleted from the adapter group.<br /><br /> The adapter name that has been deleted is contained within the "notification string" parameter.<br /><br /> This notification type is only issued to group adapters. It is not necessary to confirm this notification.|  
  
## Remarks  
 There is no online or offline notification for adapters to the group adapter. This is because control of the individual adapters is handled by each adapter itself.  
  
 In general, the notifications that require confirmation are those that are durable in the database queue. The other notifications are control and status information which are transient. Notifications that require confirmation have one of the confirm flags set.  
  
 There is no notification to or from the adapter about enabled or disabled status. This is because the enable and disable is handled by the enable and disable of the underlying configuration store application. Thus, when the adapter is disabled by an administrator, the adapter receives access denied messages from all calls to ENTSSO.  
  
## Requirements  
 **Type Library:** SSOLookup 1.0 Type Library (SSOLookup.dll)  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)
