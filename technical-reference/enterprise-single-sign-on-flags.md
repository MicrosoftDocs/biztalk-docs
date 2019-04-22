---
title: Enterprise Single Sign-On Flags
TOCTitle: Enterprise Single Sign-On Flags
ms:assetid: 3fd3c97b-c3cf-43f8-b4af-2598b8241cde
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559759(v=BTS.80)
ms:contentKeyID: 51527518
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Enterprise Single Sign-On Flags

 

The following flags are used with the Microsoft Host Integration Server Enterprise Single Sign-On (SSO) methods.

## Common flags

<table>
<thead>
<tr class="header">
<th>Member name</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>SSO_FLAG_NONE</td>
<td>0x00000000</td>
</tr>
<tr class="even">
<td>SSO_FLAG_REFRESH</td>
<td>0x00000001</td>
</tr>
<tr class="odd">
<td>SSO_FLAG_ENABLED</td>
<td>0x00000002</td>
</tr>
<tr class="even">
<td>SSO_FLAG_SSO_WINDOWS_TO_EXTERNAL</td>
<td>0x00000004</td>
</tr>
<tr class="odd">
<td>SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS</td>
<td>0x00000008</td>
</tr>
<tr class="even">
<td>SSO_FLAG_SSO_VERIFY_EXTERNAL_CREDS</td>
<td>0x00000010</td>
</tr>
<tr class="odd">
<td>SSO_FLAG_ALLOW_TICKETS</td>
<td>0x00000020</td>
</tr>
<tr class="even">
<td>SSO_FLAG_VALIDATE_TICKETS</td>
<td>0x00000040</td>
</tr>
</tbody>
</table>


## Password synchronization flags

<table>
<thead>
<tr class="header">
<th>Member name</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>SSO_FLAG_PARTIAL_SYNC_FROM_WINDOWS_TO_DB</td>
<td>0x00000100</td>
</tr>
<tr class="even">
<td>SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB</td>
<td>0x00000200</td>
</tr>
<tr class="odd">
<td>SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL</td>
<td>0x00000400</td>
</tr>
<tr class="even">
<td>SSO_FLAG_FULL_SYNC_FROM_EXTERNAL_TO_WINDOWS</td>
<td>0x00000800</td>
</tr>
<tr class="odd">
<td>SSO_FLAG_SYNC_VERIFY_EXTERNAL_CREDS</td>
<td>0x00001000</td>
</tr>
</tbody>
</table>


## Application flags

<table>
<thead>
<tr class="header">
<th>Member name</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>SSO_FLAG_APP_USES_GROUP_MAPPING</td>
<td>0x00010000</td>
</tr>
<tr class="even">
<td>SSO_FLAG_APP_EXTERNAL_NAME_SAME</td>
<td>0x00020000</td>
</tr>
</tbody>
</table>


## Mapping flags

<table>
<thead>
<tr class="header">
<th>Member name</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>SSO_FLAG_MAPPING_REQUIRES_WINDOWS_PASSWORD</td>
<td>0x01000000</td>
</tr>
<tr class="even">
<td>SSO_FLAG_MAPPING_REQUIRES_EXTERNAL_CREDS</td>
<td>0x02000000</td>
</tr>
<tr class="odd">
<td>SSO_FLAG_MAPPING_ENABLE_AUDIT</td>
<td>0x04000000</td>
</tr>
</tbody>
</table>


## Field information flags

<table>
<thead>
<tr class="header">
<th>Member name</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>SSO_FLAG_FIELD_INFO_MASK</td>
<td>0x10000000</td>
</tr>
<tr class="even">
<td>SSO_FLAG_FIELD_INFO_SYNC</td>
<td>0x20000000</td>
</tr>
</tbody>
</table>


## Property Bag flags

<table>
<thead>
<tr class="header">
<th>Member name</th>
<th>Type</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>enableApp</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_ENABLED</td>
</tr>
<tr class="even">
<td>hostInitiatedSSO</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS</td>
</tr>
<tr class="odd">
<td>validatePassword</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_SSO_VERIFY_EXTERNAL_CREDS</td>
</tr>
<tr class="even">
<td>allowTickets</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_ALLOW_TICKETS</td>
</tr>
<tr class="odd">
<td>validateTickets</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_VALIDATE_TICKETS</td>
</tr>
<tr class="even">
<td>syncFromAdapter</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB</td>
</tr>
<tr class="odd">
<td>syncToAdapter</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL</td>
</tr>
<tr class="even">
<td>changeWindowsPassword</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_FULL_SYNC_FROM_EXTERNAL_TO_WINDOWS</td>
</tr>
<tr class="odd">
<td>verifyOldPassword</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_SYNC_VERIFY_EXTERNAL_CREDS</td>
</tr>
<tr class="even">
<td>sendOldPassword</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_SYNC_PROVIDE_OLD_EXTERNAL_CREDS</td>
</tr>
<tr class="odd">
<td>allowMappingConflicts</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_SYNC_ALLOW_MAPPING_CONFLICTS</td>
</tr>
<tr class="even">
<td>groupApp</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_APP_USES_GROUP_MAPPING</td>
</tr>
<tr class="odd">
<td>groupAdapter</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_APP_GROUP</td>
</tr>
<tr class="even">
<td>allowLocalAccounts</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_APP_ALLOW_LOCAL</td>
</tr>
<tr class="odd">
<td>adminAccountSame</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_APP_ADMIN_SAME</td>
</tr>
<tr class="even">
<td>configStoreApp</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_APP_CONFIG_STORE</td>
</tr>
<tr class="odd">
<td>timeoutTickets</td>
<td>VT_BOOL</td>
<td>SSO_FLAG_APP_TICKET_TIMEOUT</td>
</tr>
<tr class="even">
<td>Description</td>
<td>VT_BSTR</td>
<td>n/a</td>
</tr>
<tr class="odd">
<td>Contact</td>
<td>VT_BSTR</td>
<td>n/a</td>
</tr>
<tr class="even">
<td>Computer</td>
<td>VT_BSTR</td>
<td>n/a</td>
</tr>
<tr class="odd">
<td>appAdminAccount</td>
<td>VT_BSTR</td>
<td>n/a</td>
</tr>
<tr class="even">
<td>appUserAccount</td>
<td>VT_BSTR</td>
<td>n/a</td>
</tr>
<tr class="odd">
<td>windowsAccount</td>
<td>VT_BSTR</td>
<td>n/a</td>
</tr>
<tr class="even">
<td>Flags</td>
<td>VT_UI4</td>
<td>n/a</td>
</tr>
<tr class="odd">
<td>flagMask</td>
<td>VT_UI4</td>
<td>n/a</td>
</tr>
<tr class="even">
<td>appTicketTimeout</td>
<td>VT_UI4</td>
<td>n/a</td>
</tr>
</tbody>
</table>


## Requirements

**Platforms:**  Windows

