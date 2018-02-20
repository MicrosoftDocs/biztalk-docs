---
title: "ISSOLookup2.LogonExternalUser Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96d95485-2558-4845-99b3-9180cb3f0d15
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
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
 [ISSOLookup2 Interface (COM)](../esso/issolookup2-interface-com.md)   
 [ISSOLookup2 Members](../esso/issolookup2-members.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)