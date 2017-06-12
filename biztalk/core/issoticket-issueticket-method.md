---
title: "ISSOTicket.IssueTicket Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1fb6fee-1415-48c8-9527-3118e1cc9043
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
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
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSOTicket Interface (COM)](../core/issoticket-interface-com.md)   
 [ISSOTicket Members](../core/issoticket-members.md)   
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)