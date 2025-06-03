---
description: "Learn more about: How to Use Password Filters"
title: "How to Use Password Filters"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Use Password Filters
The ENTSSO Password Synchronization feature synchronizes passwords between Microsoft Windows Active Directory and non-Windows systems. However, many external systems have password policy requirements which differ from those in Active Directory. (For example, an IBM system may require a password to be upper case and limited to 8 characters.) This forces ENTSSO to use the “lowest common denominator” between the two systems, limiting password security.  
  
 The ENTSSO Password Filter feature addresses this limitation. A Password Filter is merely a Password Sync Adapter with additional properties defined. These additional properties (such as maximum or minimum length, case, and character restrictions) serve to filter the passwords so that they meet the criteria of the external system.  
  
 Note that when you create a Password Filter, the Administrator group specified is automatically used as the SSO Administrators account. If you change the SSO Administrator group, you will need to make sure the Password Filter is also updated with the new SSO Administrators account.  
  
> [!NOTE]
>  As with all elements of the ENTSSO system, Password Filters contain highly sensitive information and should be exposed to the minimum number of people possible.  
  
### To Create a Password Filter  
  
1.  In the **SSO Management Console**, right-click the **Password Management** node, and then click **Create Filter**.  
  
     The **Password Filter Wizard** appears.  
  
2.  Follow the directions on the Wizard to create the Password Filter.  
  
### To Assign an Affiliate Application to a Password Filter  
  
1.  Right-click the appropriate filter, and then click **Assign**….  
  
2.  Select the appropriate **Affiliate Application**.
