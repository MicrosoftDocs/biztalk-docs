---
title: "SSO_NOTIFICATION_FLAG Enumeration (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04e95c91-8285-435a-8e55-fa5cc046c875
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# SSO_NOTIFICATION_FLAG Enumeration (COM)
Specifies the different types of flags used for Enterprise Single Sign-On (SSO).  
  
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
  
## Remarks  
 The following table describes the possible values for the notification flags.  
  
## Members  
  
|Member Name|Value|Direction|Description|  
|-----------------|-----------|---------------|-----------------|  
|**SSO_NOTIFICATION_FLAG_NONE**|0x00000000|Both|Null value.|  
|**SSO_NOTIFICATION_FLAG_ADMIN_CHANGE**|0x00000001|Both|The password change was a result of an administrator action. Some systems will be able to distinguish between an administrator action, while some will not. ENTSSO will not set this flag.<br /><br /> This flag is currently not used.|  
|**SSO_NOTIFICATION_FLAG_TEST**|0x00000008|Both|The current notification is a test request.<br /><br /> Your adapter can safely ignore this notification. You can use this notification for testing and diagnostics purposes.<br /><br /> This flag is currently not used.|  
|**SSO_NOTIFICATION_FLAG_AUDIT**|0x00000010|Both|The current request requires auditing.<br /><br /> This flag is currently not used.|  
|**SSO_NOTIFICATION_FLAG_WINDOWS**|0x00000020|Not applicable|Reserved for internal use.|  
|**SSO_NOTIFICATION_FLAG_WAIT**|0x00000040|Adapter to ENTSSO|**ReceiveNotification** should block and wait until a notification is available.<br /><br /> Best practice indicates you should set this flag and allow the PS Helper to wait for notifications.|  
|**SSO_NOTIFICATION_FLAG_SEND_ONLY**|0x00000080|Adapter to ENTSSO|Indicates that this PS Helper should initialize for sending only. It assumes that another PS Helper will be initialized normally.<br /><br /> You should use this flag when using one PS Helper for ReceiveNotification (for receiving password changes), and another fro SendNotification (for sending password changes).|  
  
## Requirements  
 **Type Library:** SSOPSHelper 1.0 Type Library (SSOPSHelper.dll)  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)