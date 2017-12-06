---
title: "ISSONotification.ReceiveNotification Method | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69f66a83-ab5c-44c9-b650-1af713d1254d
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# ISSONotification.ReceiveNotification Method
Receives a notification from the ENTSSO system, such as password changes.  
  
## Syntax  
  
```cpp#  
  
HRESULT ReceiveNotification(  
ULONG ulNotificationFlagsIn,  
SReceiveNotification* pReceiveNotification,  
GUID* pguidTrackingId  
);  
```  
  
#### Parameters  
 `bstrAdapterName`  
 [in] The unique adapter name.  
  
 `ulNotificationFlagsIn`  
 [in] The notification flags to control this notification, from the SSO_NOTIFICATION_FLAG enumeration.  
  
 `pReceiveNotification`  
 [in] Pointer for the received notification.  
  
 `pguidTrackingId`  
 [out] The tracking ID. The ENTSSO system will generate a tracking ID and return it to the caller. The tracking ID is used for auditing purposes and can also be used by the adapter to correlate responses to requests. This parameter can be NULL if the tracking ID is not required by the adapter.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed correctly. For more information, see the Error Values section.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method was successful.|  
|E_ACCESSDENIED|Access is denied.|  
|ENTSSO_E_NO_SERVER|Could not contact the ENTSSO server. Check that the ENTSSO service is running.|  
|ENTSSO_E_NO_NOTIFICATIONS|There are no notifications to be received.|  
|ENTSSO_E_WRONG_STATE|This method has been called in the wrong state.|  
  
## Remarks  
 You can use **ReceiveNotification** to receive both password changes and other notifications from the ENTSSO system.  
  
 You may call **ReceiveNotification** with or without a WAIT flag. If you specify the WAIT flag, **ReceiveNotification** blocks until a notification is available. Doing so enables you to determine if you want to dedicate a thread for receiving notifications from the ENTSSO service, or whether you want to use the event handle returned from **InitializeAdapter** to perform your own waits, shared with other events.  
  
 If **ReceiveNotification** is waiting when you call [ShutdownAdapter](../esso/issonotification-shutdownadapter-method.md), then **ReceiveNotification** returns a SHUTDOWN notification as the last notification. The SHUTDOWN notification preempts any other pending notifications.  
  
 It is possible that multiple threads could be calling **ReceiveNotification** for the same adapter name. In this case, the request is single-threaded at the ENTSSO service, and only one **ReceiveNotification** completes with valid information. The threads complete with either the next notification or NONE. The reason is that each of these threads waits for the same event.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../esso/includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSONotification Interface (COM)](../esso/issonotification-interface-com.md)   
 [ISSONotification Members](../esso/issonotification-members.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)