---
description: "Learn more about: ISSOWrapper.ShutdownAdapter Method"
title: "ISSOWrapper.ShutdownAdapter Method"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ISSOWrapper.ShutdownAdapter Method
Indicates to the ENTSSO service that the adapter is shutting down.  
  
## Syntax  
  
```cpp#  
  
HRESULT ShutDownAdapter(  
GUID* pguidTrackingId  
);  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`pguidtrackingId`|When this method returns, contains the tracking ID. The tracking ID is the same tracking ID that ENTSSO returns in the initialization process, which you can use for auditing purposes. May be NULL.|  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed correctly. For more information, see the Error Values section.  
  
## Exceptions  
 This method returns an HRESULT containing one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The shutdown was successful.|  
|E_ACCESSDENIED|Access is denied.|  
|ENTSSO_E_NO_SERVER|Could not contact the ENTSSO server. Check that the ENTSSO service is running.|  
|ENTSSO_E_WRONG_STATE|This method has been called in the wrong state.|  
  
## Remarks
