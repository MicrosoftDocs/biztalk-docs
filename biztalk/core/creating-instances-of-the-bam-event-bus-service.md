---
title: "Creating Instances of the BAM Event Bus Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 454bdde7-45a6-41ab-9196-f662273f0f2b
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating Instances of the BAM Event Bus Service
The BAM Event Bus Service runs inside a BizTalk application host. You can use the default host to host the BAM Event Bus Service, or you can create a new host. If a host hosts the BAM Event Bus service, any new instances you create for that host also hosts the service.  
  
 For information about the default host, see [Hosts](../core/hosts.md).  
  
 For information about creating hosts, see [How to Create a New Host](../core/how-to-create-a-new-host.md).  
  
 For information about creating host instances, see [How to Add a Host Instance](../core/how-to-add-a-host-instance.md).  
  
 For information about creating and configuring hosts and host instances, see [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md).  
  
### To create the host that hosts the BAM Event Bus Service  
  
1. Click **Start**, point to **All Programs**, click **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the BizTalk Administration Console window, expand the **BizTalk Server Administration** node, expand the **Biztalk Group** node and expand the **Platform Settings** node, right-click the **Hosts** node, select **New**, and then click **Host**.  
  
3. In the **Host Properties** dialog box, in the **Name** box, type a descriptive name for the host.  
  
4. On the **General** tab, select the **Allow Host Tracking** check box.  
  
    A new child node appears under the **Hosts** node with the name of the new host.  
  
5. In the **Windows group** box, type the name of the Windows group to assign this host, and then click **OK**.  
  
    A new child node appears under the **Hosts** node with the name of the new host.  
  
### To create a new host instance of the host  
  
1.  Right-click the **Host Instance** node, select **New**, and then click **Host Instance**.  
  
2.  Select a server where the host instance will run, and then click **OK**.  
  
### To add hosting tracking to the host  
  
1.  Right-click the host you want to reconfigure, and then click **Properties** .  
  
2.  On the **General** tab, select **Allow Host Tracking**, and then click **OK**.  
  
3.  Restart all instances of that host.  
  
### To remove hosting tracking from the host  
  
1.  Right-click the host from which you want to remove host tracking, and then click **Properties**.  
  
2.  Clear the **Allow Host tracking** check box, and then click **OK**.  
  
3.  Restart instances of that host.  
  
## See Also  
 [Managing the BAM Event Bus Service](../core/managing-the-bam-event-bus-service.md)   
 [BAM Security Recommendations](../core/bam-security-recommendations.md)   
 [Business Activity Monitoring (BAM)](../core/business-activity-monitoring-bam.md)