---
title: "ISSOTicket.IssueTicket Method | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52abb922-7a9b-41c1-b964-a5eafc73da7c
caps.latest.revision: 3
---
# ISSOTicket.IssueTicket Method
The **IssueTicket** method issues an Enterprise Single Sign-On (SSO) server ticket for authenticating a user on an application.  
  
## Syntax  
  
```cpp#  
  
HRESULT IssueTicket(  
LONG lFlags,  
BSTR* pbstrTicket  
);  
```  
  
#### Parameters  
 `lFlags`  
 [in]  This parameter is ignored in the current release.  
  
 `lFlags`  
 [in]  This parameter is ignored in the current release.  
  
 `pbstrTicket`  
 [out]  Pointer to a string that receives the ticket. This is a Base64-encoded value for use in XML documents.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDARG|An invalid parameter was detected.|  
  
## Remarks  
 To access this method, you must be an Application User. You can only issue a ticket for yourself.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../esso/includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSOTicket Interface (COM)](../esso/issoticket-interface-com.md)   
 [ISSOTicket Members](../esso/issoticket-members.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)