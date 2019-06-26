---
title: ISSOTicket.RedeemTicket Method
TOCTitle: ISSOTicket.RedeemTicket Method
ms:assetid: ad89b448-0064-4158-bcc0-73ef93be9993
ms:mtpsurl: https://msdn.microsoft.com/library/Aa705179(v=BTS.80)
ms:contentKeyID: 51530449
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
---

# ISSOTicket.RedeemTicket Method

 

The **RedeemTicket** method redeems an Enterprise Single Sign-On (SSO) server ticket that was previously issued with the **IssueTicket** method.

## Syntax

``` c++
  
HRESULT RedeemTicket(  
BSTR bstrApplicationName,  
BSTR bstrTicket,  
LONG lFlags,  
BSTR* pbstrExternalUserName,  
SAFEARRAY BSTR  
);  
```

#### Parameters

`bstrApplicationName`  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

`bstrTicket`  
\[in\] String that specifies the ticket value obtained from the **IssueTicket** method.

`lFlags`  
\[in\] Long integer that specifies the flags to set. Use the flag SSO\_FLAG\_REFRESH to indicate that the credential cache should be bypassed.

`pbstrExternalUserName`  
\[out\] Pointer to a string that receives the external user name associated with the ticket.

`BSTR`  
\[out\] String that receives the external credentials associated with the ticket. If there are no credentials, the size of the returned array is zero.

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

Because the credentials are returned in plain text by this method, the caller should be careful to clear (overwrite) them as soon as possible after use.

To access this method, you must be an SSO Administrator, SSO Affiliate Administrator, or an Application Administrator.

## Requirements

**Platforms:**  Windows

## See Also

[ISSOTicket Interface (COM)](issoticket-interface-com.md)  
[ISSOTicket Members](issoticket-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

