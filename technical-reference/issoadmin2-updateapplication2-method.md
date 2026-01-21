---
description: "Learn more about: ISSOAdmin2.UpdateApplication2 Method"
title: ISSOAdmin2.UpdateApplication2 Method
TOCTitle: ISSOAdmin2.UpdateApplication2 Method
ms:assetid: 5ee29a8c-9f49-47ca-b299-4307c47b23cb
ms:mtpsurl: https://msdn.microsoft.com/library/Aa771038(v=BTS.80)
ms:contentKeyID: 51528389
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
dev_langs:
- vb
- c++
---

# ISSOAdmin2.UpdateApplication2 Method

 

The UpdateApplication2 method updates the application information in the Enterprise Single Sign-On (SSO) server database.

## Syntax

``` vb
  
UpdateApplication2(  
applicationName As String,  
appInfoProps As object  
);  
```

``` c++
  
void UpdateApplication2(  
string applicationName,   
IPropertyBag appInfoProps  
);  
```

#### Parameters

`applicationName`

String containing the new application name.

`appInfoProps`

IPropertyBag containing additional application information properties. For more information, see below.

## Property Value/ Return Value

\[C++\] This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.

\[Visual Basic\] Not Applicable.

## Exceptions

\[C++\] This method returns an HRESULT containing one of the values in the following table.

\[Visual Basic\] This method indicates errors by setting the Number property of the global Err object to one of the values in the following table.

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
<td>The method succeeded</td>
</tr>
<tr class="even">
<td>E_ACCESSDENIED</td>
<td>Access is denied to the caller.</td>
</tr>
<tr class="odd">
<td>E_INVALIDREG</td>
<td>An invalid parameter was detected.</td>
</tr>
</tbody>
</table>


## Remarks

The following table describes the accepted values for appInfoProps:

<table>
<thead>
<tr class="header">
<th>propName</th>
<th>Type</th>
<th>ptrValue</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Contact</td>
<td>VT_BSTR</td>
<td>Contact name</td>
</tr>
<tr class="even">
<td>Computer</td>
<td>VT_BSTR</td>
<td>Computer name</td>
</tr>
<tr class="odd">
<td>appAdminAccount</td>
<td>VT_BSTR</td>
<td>Application admin account</td>
</tr>
<tr class="even">
<td>appUserAccount</td>
<td>VT_BSTR</td>
<td>Application user account</td>
</tr>
<tr class="odd">
<td>windowsAccount</td>
<td>VT_BSTR</td>
<td>Windows account</td>
</tr>
<tr class="even">
<td>appTicketTimeout</td>
<td>VT_UI4</td>
<td>Application ticket timeout</td>
</tr>
</tbody>
</table>


In addition, individual flags may also use the following values:

<table>
<thead>
<tr class="header">
<th>propName</th>
<th>Type</th>
<th>ptrValue</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>enableApp</td>
<td>VT_BOOL</td>
<td>Enable application</td>
</tr>
<tr class="even">
<td>hostInitiatedSSO</td>
<td>VT_BOOL</td>
<td>Host initiated SSO</td>
</tr>
<tr class="odd">
<td>validatePassword</td>
<td>VT_BOOL</td>
<td>Validate password</td>
</tr>
<tr class="even">
<td>allowTickets</td>
<td>VT_BOOL</td>
<td>Allow tickets</td>
</tr>
<tr class="odd">
<td>syncFromAdapter</td>
<td>VT_BOOL</td>
<td>Synchronize from adapter</td>
</tr>
<tr class="even">
<td>syncToAdapter</td>
<td>VT_BOOL</td>
<td>Synchronize to adapter</td>
</tr>
<tr class="odd">
<td>changeWindowsPassword</td>
<td>VT_BOOL</td>
<td>Change windows password</td>
</tr>
<tr class="even">
<td>verifyOldPassword</td>
<td>VT_BOOL</td>
<td>Verify old password</td>
</tr>
<tr class="odd">
<td>sendOldPassword</td>
<td>VT_BOOL</td>
<td>Send old password</td>
</tr>
<tr class="even">
<td>allowMappingConflicts</td>
<td>VT_BOOL</td>
<td>Allow mapping conflicts</td>
</tr>
<tr class="odd">
<td>groupApp</td>
<td>VT_BOOL</td>
<td>Group application</td>
</tr>
<tr class="even">
<td>groupAdapter</td>
<td>VT_BOOL</td>
<td>Group adapter</td>
</tr>
<tr class="odd">
<td>allowLocalAccounts</td>
<td>VT_BOOL</td>
<td>Allow local accounts</td>
</tr>
<tr class="even">
<td>adminAccountSame</td>
<td>VT_BOOL</td>
<td>Administration account same</td>
</tr>
<tr class="odd">
<td>configStoreApp</td>
<td>VT_BOOL</td>
<td>Config store application</td>
</tr>
<tr class="even">
<td>timeoutTickets</td>
<td>VT_BOOL</td>
<td>Timeout tickets</td>
</tr>
<tr class="odd">
<td>directPasswordSync</td>
<td>VT_BOOL</td>
<td>Direct password synchronization</td>
</tr>
<tr class="even">
<td>windowsCreds</td>
<td>VT_BOOL</td>
<td>Windows credentials</td>
</tr>
<tr class="odd">
<td>restrictedCreds</td>
<td>VT_BOOL</td>
<td>Restricted credentials</td>
</tr>
<tr class="even">
<td>showFilterOnly</td>
<td>VT_BOOL</td>
<td>Show filter only</td>
</tr>
<tr class="odd">
<td>restrictMappingCreate</td>
<td>VT_BOOL</td>
<td>Restrict mapping create</td>
</tr>
<tr class="even">
<td>windowsInitiatedSSO</td>
<td>VT_BOOL</td>
<td>Windows-initiated SSO</td>
</tr>
<tr class="odd">
<td>disableCredCache</td>
<td>VT_BOOL</td>
<td>Disable credentials cache</td>
</tr>
</tbody>
</table>


In addition, you may directly specify flags using the following properties:

<table>
<thead>
<tr class="header">
<th>propName</th>
<th>Type</th>
<th>ptrValue</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>flags</td>
<td>VT_UI4</td>
<td>Flags to specify</td>
</tr>
<tr class="even">
<td>flagsMask</td>
<td>VT_UI4</td>
<td>Flag mask to specify</td>
</tr>
</tbody>
</table>

