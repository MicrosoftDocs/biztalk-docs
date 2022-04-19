---
description: "Learn more about: Single Sign-On Interface"
title: "Single Sign-On Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ae99984-81a7-4351-b2b5-3f0bacc4ca7a
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Single Sign-On Interface
The following table describes the COM and .NET Framework interfaces that make up the Single Sign-On interface.  
  
|.NET|COM|Description|  
|----------|---------|-----------------|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOAdmin|[ISSOAdmin Interface (COM)](../esso/issoadmin-interface-com.md)|Creates, updates, and deletes an SSO application. Also performs other administration functions.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOConfigStore|[ISSOConfigStore Interface (COM)](../esso/issoconfigstore-interface-com.md)|Gets and sets information in the SSO configuration store.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOLookup1|[ISSOLookup1 Interface (COM)](../esso/issolookup1-interface-com.md)|Enables you to look up the external credentials on a specified application for the current user.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOLookup2|[ISSOLookup2 Interface (COM)](../esso/issolookup2-interface-com.md)|As above, but also enables you to look up the Windows credentials for a specified external user.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOMapper|[ISSOMapper Interface (COM)](../esso/issomapper-interface-com.md)|Enables you to set the external credentials for the current user for a specified application.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOMapping|[ISSOMapping Interface (COM)](../esso/issomapping-interface-com.md)|Creates and maintains the mapping between users and affiliated applications.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOTicket|[ISSOTicket Interface (COM)](../esso/issoticket-interface-com.md)|Creates the ticket that contains the appropriate security information. This ticket is then sent on with the appropriate message from your application.|  
  
 In addition, Host Integration Server supports the Password Sync Helper (PS Helper) component. You can use PS Helper when you design password synchronization components. The following table describes the COM and .NET Framework interfaces exposed by PS Helper.  
  
|.NET|COM|Description|  
|----------|---------|-----------------|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOPSWrapper|[ISSONotification Interface (COM)](../esso/issonotification-interface-com.md)|Handles password changes to and from non-Windows operating systems.|  
||[SExternalAccount Structure](../esso/sexternalaccount-structure.md)|Describes an external account.|  
||[SPasswordChange Structure (COM)](../esso/spasswordchange-structure-com.md)|Describes a password change.|  
||[SPasswordChangeComplete Structure (COM)](../esso/spasswordchangecomplete-structure-com.md)|Describes the completion of a password change.|  
||[SStatus Structure (COM)](../esso/sstatus-structure-com.md)|Describes an error or event.|  
||[SAdapterInGroup Structure (COM)](../esso/sadapteringroup-structure-com.md)|Describes the adapters in a given group.|  
||[SAdapter Structure (COM)](../esso/sadapter-structure-com.md)|Describes a specific adapter.|
