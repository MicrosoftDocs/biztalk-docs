---
title: "Single Sign-On Interface | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2e3c2d3-a7e9-4a45-965d-bfe4bf200c34
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On Interface

## Interfaces
The following table describes the COM and .NET Framework interfaces that make up the Single Sign-On interface.  
  
|.NET|COM|Description|  
|----------|---------|-----------------|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOAdmin|ISSOAdmin Interface (COM)|Creates, updates, and deletes an SSO application. Also performs other administration functions.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOConfigStore|ISSOConfigStore Interface (COM)|Gets and sets information in the SSO configuration store.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOLookup1|ISSOLookup1 Interface (COM)|Enables you to look up the external credentials on a specified application for the current user.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOLookup2|ISSOLookup2 Interface (COM)|As above, but also enables you to look up the Windows credentials for a specified external user.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOMapper|ISSOMapper Interface (COM)|Enables you to set the external credentials for the current user for a specified application.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOMapping|ISSOMapping Interface (COM)|Creates and maintains the mapping between users and affiliated applications.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOTicket|ISSOTicket Interface (COM)|Creates the ticket that contains the appropriate security information. This ticket is then sent on with the appropriate message from your application.|  


## Password Sync Helper  
 In addition, Host Integration Server supports the Password Sync Helper (PS Helper) component. You can use PS Helper when you design password synchronization components. The following table describes the COM and .NET Framework interfaces exposed by PS Helper.  
  
|.NET|COM|Description|  
|----------|---------|-----------------|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOPSWrapper|ISSONotification Interface (COM)|Handles password changes to and from non-Windows operating systems.|  
||SExternalAccount Structure (COM)|Describes an external account.|  
||SPasswordChange Structure (COM)|Describes a password change.|  
||SPasswordChangeComplete Structure (COM)|Describes the completion of a password change.|  
||SStatus Structure (COM)|Describes an error or event.|  
||SAdapterInGroup Structure (COM)|Describes the adapters in a given group.|  
||SAdapter Structure (COM)|Describes a specific adapter.|

## See also
See the SSO COM objects [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 