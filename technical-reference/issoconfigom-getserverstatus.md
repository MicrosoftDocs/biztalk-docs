---
description: "Learn more about: ISSOConfigOM.GetServerStatus"
title: ISSOConfigOM.GetServerStatus
TOCTitle: ISSOConfigOM.GetServerStatus
ms:assetid: 9cbc817c-108c-4a5e-a3cf-c7f1354d80e6
ms:mtpsurl: https://msdn.microsoft.com/library/Aa705006(v=BTS.80)
ms:contentKeyID: 51530006
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
dev_langs:
- vb
- c++
---

# ISSOConfigOM.GetServerStatus

 

The **GetServerStatus** method describes the status of the current server.

## Syntax

``` vb
  
GetServerStatus(  
flags As Integer,   
ssoServerName As String,   
sqlServer As String,   
sqlDatabase As String,   
serviceAccount As String,   
computerNameCluster As String,   
computerNameNode As String,   
eventCountInformational As Integer,   
eventCountWarning As Integer,   
eventCountError As Integer,   
versionInfoM As Integer,   
versionInfoL As Integer,   
auditLevelN As Integer,   
auditLevelP As Integer,   
passwordSyncAge As Integer,   
statusFlags As Integer  
);  
  
```

``` c++
  
HRESULT GetServerStatus(  
int flags,   
BSTR ssoServerName,   
BSTR sqlServer,   
BSTR sqlDatabase,   
BSTR serviceAccount,   
BSTR computerNameCluster,   
BSTR computerNameNode,   
BSTR eventCountInformational,   
int eventCountWarning,   
int eventCountError,   
int versionInfoM,   
int versionInfoL,   
int auditLevelN,   
int auditLevelP,   
int passwordSyncAge,   
int statusFlags  
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
<td><code>flags</code></td>
<td>Not used in this version. Should be set to zero.</td>
</tr>
<tr class="even">
<td><code>ssoServerName</code></td>
<td>Returns a string containing the current SSO server name.</td>
</tr>
<tr class="odd">
<td><code>sqlServer</code></td>
<td>Returns a string containing the name of the SQL server of the current server.</td>
</tr>
<tr class="even">
<td><code>sqlDatabase</code></td>
<td>Returns a string containing the name of the SQL database of the current server.</td>
</tr>
<tr class="odd">
<td><code>serviceAccount</code></td>
<td>Returns a string containing the current service account.</td>
</tr>
<tr class="even">
<td><code>computerNameCluster</code></td>
<td>Returns a string containing the name of the current computer cluster.</td>
</tr>
<tr class="odd">
<td><code>computerNameNode</code></td>
<td>Returns the name of the current computer.</td>
</tr>
<tr class="even">
<td><code>eventCountInformational</code></td>
<td>Returns an integer containing information regarding the event count.</td>
</tr>
<tr class="odd">
<td><code>eventCountWarning</code></td>
<td>Returns an integer containing the event count warning.</td>
</tr>
<tr class="even">
<td><code>eventCountError</code></td>
<td>Returns an integer containing the event count error.</td>
</tr>
<tr class="odd">
<td><code>versionInfoM</code></td>
<td>Returns an integer containing the MSB version info.</td>
</tr>
<tr class="even">
<td><code>versionInfoL</code></td>
<td>Returns an integer containing the LSB version info.</td>
</tr>
<tr class="odd">
<td><code>auditLevelN</code></td>
<td>Returns an integer containing the negative audit level.</td>
</tr>
<tr class="even">
<td><code>auditLevelP</code></td>
<td>Returns an integer containing the positive audit level.</td>
</tr>
<tr class="odd">
<td><code>passwordSyncAge</code></td>
<td>Returns an integer containing the password sync age.</td>
</tr>
<tr class="even">
<td><code>statusFlags</code></td>
<td>Returns an integer containing the status flags. For more information, see SSOStatusFlags.</td>
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

