---
description: "Learn more about: ISSOTicket.IssueTicket Method"
title: ISSOTicket.IssueTicket Method
TOCTitle: ISSOTicket.IssueTicket Method
ms:assetid: e1fb6fee-1415-48c8-9527-3118e1cc9043
ms:mtpsurl: https://msdn.microsoft.com/library/Aa705430(v=BTS.80)
ms:contentKeyID: 51532905
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
dev_langs:
- c++
---

# ISSOTicket.IssueTicket Method

 

The **IssueTicket** method issues an Enterprise Single Sign-On (SSO) server ticket for authenticating a user on an application.

## Syntax

``` c++
  
HRESULT IssueTicket(  
LONG lFlags,  
BSTR* pbstrTicket  
);  
```

#### Parameters

`lFlags`  
\[in\] This parameter is ignored in the current release.

`lFlags`  
\[in\] This parameter is ignored in the current release.

`pbstrTicket`  
\[out\] Pointer to a string that receives the ticket. This is a Base64-encoded value for use in XML documents.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.

## Error Values

This method returns an HRESULT containing one of the values in the following table.

<table>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>S_OK</td>
<td>The method succeeded.</td>
</tr>
<tr class="even">
<td>E_ACCESSDENIED</td>
<td>Access is denied to the caller.</td>
</tr>
<tr class="odd">
<td>E_INVALIDARG</td>
<td>An invalid parameter was detected.</td>
</tr>
</tbody>
</table>


## Remarks

To access this method, you must be an Application User. You can only issue a ticket for yourself.

## Requirements

**Platforms:**  Windows

## See Also

[ISSOTicket Interface (COM)](issoticket-interface-com.md)  
[ISSOTicket Members](issoticket-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

