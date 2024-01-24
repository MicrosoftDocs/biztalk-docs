---
description: "Learn more about: How to Create a Cluster Group with a Disk, IP Address, and Name Resource"
title: "How to Create a Cluster Group with a Disk, IP Address, and Name Resource1"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Create a Cluster Group with a Disk, IP Address, and Name Resource
For clustered [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components and dependencies to be accessible over the network via NetBIOS, a clustered **Network Name** resource must be created in same cluster group. For a clustered Network Name resource to be accessible via the TCP/IP protocol, an **IP Address** resource must be created in the same cluster group as well. Some [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dependencies also require the use of a clustered **Physical Disk** resource to function correctly. To create a cluster group with a **Physical Disk**, **IP Address** and **Network Name** resource follow these steps:  
  
### To create a service or application with a Physical Disk, IP Address, and Network Name resource  
  
1.  In Windows, click **Start**, **Programs**, **Administrative Tools**, and then **Failover Cluster Management** to start the Failover Cluster Management program.  
  
2.  Fail over all services and applications to the cluster node that you are running Failover Cluster Management on. To fail over a service or application, right click the service or application in the left pane of Failover Cluster Management, point to **Move this service or application to another node** and click to select the destination node.  
  
    > [!NOTE]
    >  The cluster node that hosts running cluster resources is also known as the **active** node. The cluster node that hosts non-running cluster resources is also known as the **passive** node.  
  
3.  In the left-hand pane, right-click **Services and Applications**, click **Configure a Service or Application** to launch the High Availability Wizard, and then click **Next**.  
  
4.  Click to select **File Server** and click **Next**.  
  
    > [!NOTE]
    >  Selecting **File Server** at this point is done as a straightforward way to create a cluster group with a disk resource.  
  
5.  On the **Client Access Point** page of the High Availability Wizard enter a unique network name into the **Name** box, for example *BizTalkCluster*, enter an available IP address under **Address**, and then click **Next**.  
  
6.  On the **Select Storage** page, click to select an available disk resource and then click **Next**.  
  
7.  On the **Confirmation** page click **Next** to create the cluster group.  
  
8.  On the **Summary** page click **Finish**.
