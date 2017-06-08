---
title: "Enterprise Single Sign-On Flags | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3fd3c97b-c3cf-43f8-b4af-2598b8241cde
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Enterprise Single Sign-On Flags
The following flags are used with the Microsoft Host Integration Server Enterprise Single Sign-On (SSO) methods.  
  
## Common flags  
  
|Member name|Value|  
|-----------------|-----------|  
|SSO_FLAG_NONE|0x00000000|  
|SSO_FLAG_REFRESH|0x00000001|  
|SSO_FLAG_ENABLED|0x00000002|  
|SSO_FLAG_SSO_WINDOWS_TO_EXTERNAL|0x00000004|  
|SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS|0x00000008|  
|SSO_FLAG_SSO_VERIFY_EXTERNAL_CREDS|0x00000010|  
|SSO_FLAG_ALLOW_TICKETS|0x00000020|  
|SSO_FLAG_VALIDATE_TICKETS|0x00000040|  
  
## Password synchronization flags  
  
|Member name|Value|  
|-----------------|-----------|  
|SSO_FLAG_PARTIAL_SYNC_FROM_WINDOWS_TO_DB|0x00000100|  
|SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB|0x00000200|  
|SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL|0x00000400|  
|SSO_FLAG_FULL_SYNC_FROM_EXTERNAL_TO_WINDOWS|0x00000800|  
|SSO_FLAG_SYNC_VERIFY_EXTERNAL_CREDS|0x00001000|  
  
## Application flags  
  
|Member name|Value|  
|-----------------|-----------|  
|SSO_FLAG_APP_USES_GROUP_MAPPING|0x00010000|  
|SSO_FLAG_APP_EXTERNAL_NAME_SAME|0x00020000|  
  
## Mapping flags  
  
|Member name|Value|  
|-----------------|-----------|  
|SSO_FLAG_MAPPING_REQUIRES_WINDOWS_PASSWORD|0x01000000|  
|SSO_FLAG_MAPPING_REQUIRES_EXTERNAL_CREDS|0x02000000|  
|SSO_FLAG_MAPPING_ENABLE_AUDIT|0x04000000|  
  
## Field information flags  
  
|Member name|Value|  
|-----------------|-----------|  
|SSO_FLAG_FIELD_INFO_MASK|0x10000000|  
|SSO_FLAG_FIELD_INFO_SYNC|0x20000000|  
  
## Property Bag flags  
  
|Member name|Type|Value|  
|-----------------|----------|-----------|  
|enableApp|VT_BOOL|SSO_FLAG_ENABLED|  
|hostInitiatedSSO|VT_BOOL|SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS|  
|validatePassword|VT_BOOL|SSO_FLAG_SSO_VERIFY_EXTERNAL_CREDS|  
|allowTickets|VT_BOOL|SSO_FLAG_ALLOW_TICKETS|  
|validateTickets|VT_BOOL|SSO_FLAG_VALIDATE_TICKETS|  
|syncFromAdapter|VT_BOOL|SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB|  
|syncToAdapter|VT_BOOL|SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL|  
|changeWindowsPassword|VT_BOOL|SSO_FLAG_FULL_SYNC_FROM_EXTERNAL_TO_WINDOWS|  
|verifyOldPassword|VT_BOOL|SSO_FLAG_SYNC_VERIFY_EXTERNAL_CREDS|  
|sendOldPassword|VT_BOOL|SSO_FLAG_SYNC_PROVIDE_OLD_EXTERNAL_CREDS|  
|allowMappingConflicts|VT_BOOL|SSO_FLAG_SYNC_ALLOW_MAPPING_CONFLICTS|  
|groupApp|VT_BOOL|SSO_FLAG_APP_USES_GROUP_MAPPING|  
|groupAdapter|VT_BOOL|SSO_FLAG_APP_GROUP|  
|allowLocalAccounts|VT_BOOL|SSO_FLAG_APP_ALLOW_LOCAL|  
|adminAccountSame|VT_BOOL|SSO_FLAG_APP_ADMIN_SAME|  
|configStoreApp|VT_BOOL|SSO_FLAG_APP_CONFIG_STORE|  
|timeoutTickets|VT_BOOL|SSO_FLAG_APP_TICKET_TIMEOUT|  
|Description|VT_BSTR|n/a|  
|Contact|VT_BSTR|n/a|  
|Computer|VT_BSTR|n/a|  
|appAdminAccount|VT_BSTR|n/a|  
|appUserAccount|VT_BSTR|n/a|  
|windowsAccount|VT_BSTR|n/a|  
|Flags|VT_UI4|n/a|  
|flagMask|VT_UI4|n/a|  
|appTicketTimeout|VT_UI4|n/a|  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]