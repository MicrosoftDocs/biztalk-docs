---
description: "Learn more about: ISSOWrapper.SendNotification Method"
title: "ISSOWrapper.SendNotification Method"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ISSOWrapper.SendNotification Method
Sends a notification from the adapter to the ENTSSO service.  
  
## Syntax  
  
```cpp#  
  
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
  
|Parameter|Description|  
|---------------|-----------------|  
|`ulNotificationType`|Notification type.|  
|`ulNotificationFlags`|Notification flags.|  
|`guidTrackingIdIn`|The tracking id of the password change to be confirmed.|  
|`bstrExternalAccount`|The external account for which the password has changed.|  
|`bstrNewExternalPassword`|The new password for the external account.|  
|`bstrOldExternalPassword`|Optional. The old password for the external account.|  
|`ullTimestamp`|The timestamp when the password change was made, or zero to use the current time.|  
|`ullErrorCode`|If non-zero, the external password change failed. errorCode will be written to the event log. Zero for successful external password changes.|  
|`bstrErrorMessage`|Optional. The message to write to the event log if the password change failed.|  
|`pguidTrackingIdOut`|Optional. On return, contains a pointer to a GUID to receive the tracking id.|  
  
## Property Value/Return Value  
 E_ACCESS_DENIED  
 Access is denied.  
  
## Exceptions  
  
## Remarks  
 SendNotification uses different parameters depending on the notificationType. The following table describes the necessary parameters for each type of notification.  
  
|notificationType|Parameters|  
|----------------------|----------------|  
|SSO_NOTIFICATION_TYPE_PASSWORD_CHANGE|externalAccount<br /><br /> newExternalPassword<br /><br /> oldExternalPassword<br /><br /> timestamp|  
|SSO_NOTIFICATION_TYPE_PASSWORD_CHANGE_COMPLETE|trackingIdIn<br /><br /> errorCode<br /><br /> errorMessage|  
|SSO_NOTIFICATION_TYPE_STATUS_OFFLINE|errorCode<br /><br /> errorMessage|  
|SSO_NOTIFICATION_TYPE_PASSWORD_EXPIRED|externalAccount|  
|SSO_NOTIFICATION_TYPE_STATUS_REQUEST|None|  
|SSO_NOTIFICATION_TYPE_STATUS_ONLINE|None|  
  
## Requirements
