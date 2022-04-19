---
description: "Learn more about: ISSOAdmin2.GetApplicationInfo2 Method"
title: "ISSOAdmin2.GetApplicationInfo2 Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 389b9812-a4e2-4c22-bf08-d9d37ca09693
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# ISSOAdmin2.GetApplicationInfo2 Method
The **GetApplicationInfo2** method gets the application information from the Enterprise Single Sign-On (SSO) server database.  
  
## Syntax  
  
```vb  
  
GetApplicationInfo2(  
applicationName As String,   
appInfoProps As object  
)  
  
```  
  
```cpp#  
  
HRESULT GetApplicationInfo2(  
BSTR applicationName,   
IPropertyBag* appInfoProps  
)  
```  
  
#### Parameters  
 `applicationName`  
  
 String containing the name of the application.  
  
 `appInfoProps`  
  
 IPropertyBag containing additional application information properties. For more information, see below.  
  
## Property Value/ Return Value  
 [C++] This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 [Visual Basic] Not Applicable.  
  
## Exceptions  
 [C++] This method returns an HRESULT containing one of the values in the following table.  
  
 [Visual Basic] This method indicates errors by setting the Number property of the global Err object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDREG|An invalid parameter was detected.|  
  
## Remarks  
 The following table describes the accepted values for appInfoProps:  
  
|propName|Type|ptrValue|  
|--------------|----------|--------------|  
|Contact|VT_BSTR|Contact name|  
|Computer|VT_BSTR|Computer name|  
|appAdminAccount|VT_BSTR|Application admin account|  
|appUserAccount|VT_BSTR|Application user account|  
|windowsAccount|VT_BSTR|Windows account|  
|appTicketTimeout|VT_UI4|Application ticket timeout|  
  
 In addition, individual flags may also use the following values:  
  
|propName|Type|ptrValue|  
|--------------|----------|--------------|  
|enableApp|VT_BOOL|Enable application|  
|hostInitiatedSSO|VT_BOOL|Host initiated SSO|  
|validatePassword|VT_BOOL|Validate password|  
|allowTickets|VT_BOOL|Allow tickets|  
|syncFromAdapter|VT_BOOL|Synchronize from adapter|  
|syncToAdapter|VT_BOOL|Synchronize to adapter|  
|changeWindowsPassword|VT_BOOL|Change windows password|  
|verifyOldPassword|VT_BOOL|Verify old password|  
|sendOldPassword|VT_BOOL|Send old password|  
|allowMappingConflicts|VT_BOOL|Allow mapping conflicts|  
|groupApp|VT_BOOL|Group application|  
|groupAdapter|VT_BOOL|Group adapter|  
|allowLocalAccounts|VT_BOOL|Allow local accounts|  
|adminAccountSame|VT_BOOL|Administration account same|  
|configStoreApp|VT_BOOL|Config store application|  
|timeoutTickets|VT_BOOL|Timeout tickets|  
|directPasswordSync|VT_BOOL|Direct password synchronization|  
|windowsCreds|VT_BOOL|Windows credentials|  
|restrictedCreds|VT_BOOL|Restricted credentials|  
|showFilterOnly|VT_BOOL|Show filter only|  
|restrictMappingCreate|VT_BOOL|Restrict mapping create|  
|windowsInitiatedSSO|VT_BOOL|Windows-initiated SSO|  
|disableCredCache|VT_BOOL|Disable credentials cache|
