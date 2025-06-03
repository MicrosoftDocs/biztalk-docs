---
description: "Learn more about: How to Restore Applications and Enable Processing"
title: "How to Restore Applications and Enable Processing"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Restore Applications and Enable Processing
Configure the applications in the BizTalk group and enable application processing after following the steps described in the topic [How to Update the Runtime Computers](../technical-guides/how-to-update-the-runtime-computers.md).  
  
### To enable application configuration and restore application processing  
  
1. Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application Installation MSI file on each BizTalk server in the group.  
  
2. Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application Configuration MSI file on one server in the group to configure the application for the disaster recovery site. The names for receive locations and send ports remain the same. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application Configuration MSI file updates bindings so that these artifacts point to the correct locations in the disaster recovery environment.  
  
   > [!NOTE]  
   >  If receive locations and send ports are not affected by the loss of the production site, it may not be necessary to reconfigure the application with disaster recovery-specific locations.  
  
3. Restore application processing by enabling all application receive locations, send ports, and host instances.  
  
## See Also  
 [Recovering the Runtime Computers](../technical-guides/recovering-the-runtime-computers.md)
