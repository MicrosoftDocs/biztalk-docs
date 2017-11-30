---
title: "Create New Password Sync Adapter Wizard: Options2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts06.esso.pws.wizard.options"
ms.assetid: 948c9370-746b-4588-8e00-a47a13cd8f72
caps.latest.revision: 4
---
# Create New Password Sync Adapter Wizard: Options
Specify options for the new Password Sync Adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Enabled**|Determines whether the adapter is enabled.|  
|**Receive password changes from adapter**|Determines whether the adapter is allowed to receive external password changes. Default is not selected.|  
|**Verify old password**|Determines whether the adapter will verify the old password when an external password change is received. If this option is selected then with an external password change the external adapter must supply the old external password as well as the new external password. The old external password is then compared with the existing external password in the Enterprise Single Sign-On (SSO) database for that external account. If they match, the password change is accepted. If they do not match, the password change is rejected. Default is selected.|  
|**Change Windows password**|Determines whether the Windows password in Active Directory will also be changed when an external password change is received (full sync). Default is not selected.|  
|**Send Windows password changes to adapter**|Determines whether Windows password changes made in Active Directory will be sent to the external adapter. Default is not selected.|  
|**Send old password to adapter**|If selected, the old password value (from the SSO database) will also be sent to the external adapter as well as the new password value. Some external systems might require both the old and new password values to change the password. Default is not selected.|  
|**Allow mapping conflicts**|Determines whether the adapter will allow mapping conflicts.<br /><br /> A mapping conflict occurs when mappings are not unique. In a single SSO Individual application, mappings are always one-to-one: one Windows account is mapped to exactly one external account and vice versa.<br /><br /> However, it is possible to assign more than one application to an adapter. Thus, it is possible to have a mapping in one application that conflicts with a mapping in the other.<br /><br /> This purpose of this option is to prevent this from occurring. It is more secure to not allow mapping conflicts unless there is a specific, well understood requirement for this behavior.<br /><br /> Default is not selected.|  
  
## See Also  
 [Enterprise Single Sign-On (Configuration)](../HIS2010/enterprise-single-sign-on-configuration-2.md)   
 [Create New Password Sync Adapter Wizard](../HIS2010/create-new-password-sync-adapter-wizard2.md)