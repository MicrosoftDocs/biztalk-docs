---
description: "Learn more about: ISSOLookup2.LogonExternalUser Method"
title: ISSOLookup2.LogonExternalUser Method
TOCTitle: ISSOLookup2.LogonExternalUser Method
ms:assetid: 0faa99de-77b7-4583-8284-57f609e707d9
ms:mtpsurl: https://msdn.microsoft.com/library/Aa744687(v=BTS.80)
ms:contentKeyID: 51526261
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOLookup2.LogonExternalUser Method

 

The **LogonExternalUser** method logs on an external user.

## Syntax

``` c++
  
Int GetCredentials(  
BSTR bstrApplicationName,   
BSTR bstrUserName,  
LONG lFlags,  
Array ppsaCredentials  
);  
```

``` vb
  
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
\[in\] String that specified the name of the application to log on to.

`bstrApplicationName`  
\[in\] String that specified the name of the application to log on to.

`bstrUserName`  
\[in\] String that specified the name of the external user to log on.

`bstrUserName`  
\[in\] String that specified the name of the external user to log on.

`lFlags`  
\[in\] Long integer that specifies the flags to set.

`lFlags`  
\[in\] Long integer that specifies the flags to set.

`ppsaCredentials`  
Array that holds the credentials of the user.

`ppsaCredentials`  
Array that holds the credentials of the user.

## Return Value

A windows handle.

A windows handle.

## Requirements

**Platforms:**  Windows

## See Also

[ISSOLookup2 Interface (COM)](issolookup2-interface-com.md)  
[ISSOLookup2 Members](issolookup2-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

