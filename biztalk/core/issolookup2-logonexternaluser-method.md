---
title: "ISSOLookup2.LogonExternalUser Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0faa99de-77b7-4583-8284-57f609e707d9
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ISSOLookup2.LogonExternalUser Method
The **LogonExternalUser** method logs on an external user.  
  
## Syntax  
  
```cpp#  
  
Int GetCredentials(  
BSTR bstrApplicationName,   
BSTR bstrUserName,  
LONG lFlags,  
Array ppsaCredentials  
);  
```  
  
```vb  
  
Function GetCredentials(  
bstrApplicationName As String,  
bstrUserName As String,   
lFlags As Long,  
ppsaCredentials As String  
)  
As Integer  
```  
  
#### Parameters  
 `bstrApplicationName`  
 [in]  String that specified the name of the application to log on to.  
  
 `bstrApplicationName`  
 [in]  String that specified the name of the application to log on to.  
  
 `bstrUserName`  
 [in]  String that specified the name of the external user to log on.  
  
 `bstrUserName`  
 [in]  String that specified the name of the external user to log on.  
  
 `lFlags`  
 [in] Long integer that specifies the flags to set.  
  
 `lFlags`  
 [in] Long integer that specifies the flags to set.  
  
 `ppsaCredentials`  
 Array that holds the credentials of the user.  
  
 `ppsaCredentials`  
 Array that holds the credentials of the user.  
  
## Return Value  
 A windows handle.  
  
 A windows handle.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSOLookup2 Interface (COM)](../core/issolookup2-interface-com.md)   
 [ISSOLookup2 Members](../core/issolookup2-members.md)   
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)