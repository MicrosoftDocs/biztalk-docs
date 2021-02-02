---
description: "Learn more about: ISSOWrapper.ReceiveNotification Method"
title: "ISSOWrapper.ReceiveNotification Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 105890d8-6d21-49e0-8e08-430cea64a018
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# ISSOWrapper.ReceiveNotification Method
Receives a notification to the adapter from the ENTSSO service.  
  
## Syntax  
  
```cpp#  
  
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
  
|Parameter|Description|  
|---------------|-----------------|  
|`ulNotificationFlagsIn`|The notification flags. Specify SSO_NOTIFICATION_FLAG_WAIT if you want your call to block waiting for a notification, or SSO_NOTIFICATION_FLAG_NONE.|  
|`guidTrackingIdIn`|The tracking ID.|  
|`pulNnotificationType`|On return, contains a pointer to a ULONG that will receive the notification type.|  
|`pulNotificationFlagsOut`|On return, contains a pointer to a ULONG that will receive the notification flags|  
|`pbstrExternalAccount`|On return, contains the external account for which the password should be changed.|  
|`newExternalPassword`|On return, contains the new password for the external account.|  
|`pbstrOldExternalPassword`|Optional. On return, contains the old password for the external account.|  
|`pullTimestamp`|On return, contains the timestamp when the password change was made.|  
|`pullErrorCode`|On return, contains the error code.|  
|`pbstrErrorMessage`|On return, contains an error message.|  
|`ppsaAdapters`|On return, contains an array of adapter names.|  
|`pbstrAdapterName`|On return, contains the adapter name.|  
|`pbuidTrackingIdOut`|On return, contains the tracking ID.|  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed correctly. For more information, see the Exceptions section.  
  
## Exceptions  
 E_ACCESS_DENIED  
 Access is denied.  
  
## Remarks  
 ReceiveNotification uses different parameters to return information depending on the notificationType. The following table describes the relationship between the different parameters and types of notifications.  
  
|notificationType|Parameters|  
|----------------------|----------------|  
|SSO_NOTIFICATION_TYPE_PASSWORD_CHANGE|externalAccount<br /><br /> newExternalPassword<br /><br /> oldExternalPassword<br /><br /> timestamp|  
|SSO_NOTIFICATION_TYPE_PASSWORD_CHANGE_COMPLETE|trackingIdIn<br /><br /> errorCode<br /><br /> errorMessage|  
|SSO_NOTIFICATION_TYPE_STATUS_OFFLINE|errorCode<br /><br /> errorMessage|  
|SSO_NOTIFICATION_TYPE_PASSWORD_EXPIRED|externalAccount|  
|SSO_NOTIFICATION_TYPE_STATUS_REQUEST|None|  
|SSO_NOTIFICATION_TYPE_STATUS_ONLINE|None|
