---
title: "ISSONotification.ShutdownAdapter Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5110a66-ca8c-4866-a7c3-4ab4e8684561
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ISSONotification.ShutdownAdapter Method
Indicates that the password sync adapter is shutting down.  
  
## Syntax  
  
```cpp#  
  
HRESULT ShutDownAdapter(  
GUID* pguidTrackingId   
);  
```  
  
#### Parameters  
 `pguidTrackingId`  
 [out] When this method returns, contains the tracking ID. The tracking ID is the same tracking ID that ENTSSO returns in the initialization process, which you can use for auditing purposes. May be NULL.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed correctly. For more information, see the Error Values section.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The shutdown was successful.|  
|E_ACCESSDENIED|Access is denied.|  
|ENTSSO_E_NO_SERVER|Could not contact the ENTSSO server. Check that the ENTSSO service is running.|  
|ENTSSO_E_WRONG_STATE|This method has been called in the wrong state.|  
  
## Remarks  
 **ShutdownAdapter** should be the last method you call. You may call neither [SendNotification](../esso/issonotification-sendnotification-method.md) nor [ReceiveNotification](../esso/issonotification-receivenotification-method.md) after you call **ShutdownAdapter.** The only method you may call afterward is [InitializeAdapter](../esso/issonotification-initializeadapter-method.md), which initializes a new session.  
  
 Calls to **SendNotification** or **ReceiveNotification** that are in progress (on other threads) when you call **ShutdownAdapter** may receive ENTSSO_E_WRONG_STATE, although one thread calling **ReceiveNotification** receives the SHUTDOWN_COMPLETE notification.  
  
 **ShutdownAdapter** is single-threaded. ENTSSO blocks all other threads calling **ShutdownAdapter** until **ShutdownAdapter** has completed. **ShutdownAdapter** is also synchronized with the **InitializeAdapter** method.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSONotification Interface (COM)](../esso/issonotification-interface-com.md)   
 [ISSONotification Members](../esso/issonotification-members.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)