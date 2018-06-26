---
title: "Run As Profiles | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98ac0a0c-91d8-4d12-aa40-2ad2e29ec784
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Run As Profiles
When the BizTalk Server Core Library Management Pack is first imported, it creates two new Run As Profiles:  
  
- **BizTalk Server Discovery Account**. This profile is associated with all discoveries of BizTalk Server role components.  
  
- **BizTalk Server Monitoring Account**. This profile is associated with all monitors and tasks.  
  
  By default, all discoveries, monitors, and tasks defined in the BizTalk Server Management Packs default to using the accounts defined in the “Default Action Account” Run As Profile.  If the default action account for a given system does not have the necessary permissions to discover or monitor BizTalk, then those systems can be bound to more specific credentials in the BizTalk Server Run As Profiles, which do have access to BizTalk Server.  
  
  The following are the generic steps to configure Run As Profiles for BizTalk Server:  
  
### To configure Run As profiles  
  
1.  Identify the name(s) of the target computer(s) where the default action account has insufficient rights to monitor BizTalk Server.  
  
2.  For each system create or use an existing set of credentials that have at least the BizTalk Server privileges discussed in the [Low-Privilege Environments](../technical-guides/low-privilege-environments.md) section of this management pack guide.  
  
3.  For each set of credentials identified in step 2, make sure that a corresponding Run As Account exists in the management group. Create the Run As Account if it is necessary.  
  
4.  Set up the mappings between the targets and the Run As Account(s) on the **Run As Accounts** tab of each of the Run As Profiles.