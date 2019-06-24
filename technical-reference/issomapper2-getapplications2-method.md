---
title: ISSOMapper2.GetApplications2 Method
TOCTitle: ISSOMapper2.GetApplications2 Method
ms:assetid: 8eca0fe4-e178-4267-a510-6ed42a33f011
ms:mtpsurl: https://msdn.microsoft.com/library/Aa745609(v=BTS.80)
ms:contentKeyID: 51529632
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
- csharp
---

# ISSOMapper2.GetApplications2 Method

 

The GetApplications2 method retrieves the available applications for a Microsoft Windows user.

## Syntax

``` vb
  
Sub GetApplications2(  
applications As String,   
descriptions As String,   
contactInfo As String,   
userAccounts As String,   
adminAccounts As String,   
flags As Long  
);  
```

``` csharp
  
HRESULT GetApplications2(  
SAFEARRAY applications,   
SAFEARRAY descriptions,   
SAFEARRAY contactInfo,   
SAFEARRAY userAccounts,   
SAFEARRAY adminAccounts,   
SAFEARRAY flags  
);  
```

#### Parameters

<table>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><code>applications</code></td>
<td>String array that returns the application name.</td>
</tr>
<tr class="even">
<td><code>descriptions</code></td>
<td>String array that returns a description of the application.</td>
</tr>
<tr class="odd">
<td><code>contactInfo</code></td>
<td>String array that returns the contact information for the application.</td>
</tr>
<tr class="even">
<td><code>userAccounts</code></td>
<td>String array that returns all user accounts for the application. GetApplications2 returns a null in this parameter when called by an application user.</td>
</tr>
<tr class="odd">
<td><code>adminAccounts</code></td>
<td>String array that returns all administration accounts for the application. GetApplications2 returns a null in this parameter when called by an application user.</td>
</tr>
<tr class="even">
<td><code>flags</code></td>
<td>Integer array that returns the flags for the application.</td>
</tr>
</tbody>
</table>


## Property Value/Return Value

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
<td>The method succeeded.</td>
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

