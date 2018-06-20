---
title: "How to Configure a BizTalk Host as a Cluster Resource1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installation, high availability"
  - "clustering, servers"
  - "hosts, multiple"
  - "hosts, high availability"
  - "Windows Server cluster"
  - "databases, clustering"
  - "clustering, fail-overs"
  - "Windows Server cluster, about Windows Server cluster"
  - "installation, planning"
  - "clustering, databases"
  - "clustering, best practices"
  - "clustering, unclustering"
  - "clustering, configuring"
  - "installation, clustering"
ms.assetid: bcd656d2-8dd6-49fc-9c42-ef5c884e52c4
caps.latest.revision: 36
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a BizTalk Host as a Cluster Resource
This topic discusses the steps that you must follow to configure a BizTalk host as a cluster resource. To complete the steps in this topic, you must have already configured at least two BizTalk Servers in a BizTalk group as members of a Windows Server cluster. For more information about configuring a Windows Server cluster, see the Windows Server online Help.  
  
## Prerequisites  
 You must be logged on as a member of the BizTalk Administrators group to cluster or uncluster a host.  
  
## Considerations and Known Issues  
  
- A BizTalk Server must be configured as a node in a Windows Server failover cluster before you can run an instance of a clustered BizTalk host on the BizTalk Server. For more information about configuring a cluster node in a server cluster, see the Windows Server online Help.  
  
- You cannot fail over a clustered BizTalk host to a host instance that has the option **Disable host instance from starting** set. Ensure that all host instances for the clustered BizTalk host do not have this option enabled. This option is set in the BizTalk Server Administration console on the **Host Instance Properties** page.  
  
- When you cluster a BizTalk host, a corresponding cluster resource is created in the specified cluster resource group. When the cluster resource is created, each available node of the cluster is added as a possible owner of the cluster resource. Since a cluster resource can be failed over to any node in the list of possible owners, you should add an instance of the host to all available nodes of a cluster before clustering a BizTalk host. Attempts to fail over a clustered BizTalk host to a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer that does not contain an instance of the host will fail.  
  
  > [!NOTE]
  >  If you want to prevent a clustered BizTalk host from running on or failing over to a particular cluster node, remove the node from the list of possible owners of the clustered resource that is created when you cluster the BizTalk host. You can modify the list of possible owners of a cluster resource using the Windows Server Failover Cluster Management interface.  
  
- When clustering a BizTalk host, ensure that the cluster group, clustered service or application  that you are adding the host to contains a Network Name and IP Address resource. If the target cluster group contains a Network Name and IP Address resource, then the Network Name resource is added as a dependency to the clustered BizTalk host. If these resources are not available, then the BizTalk host will not function correctly as a clustered resource.  
  
- If you unconfigure a BizTalk server/cluster node that is listed as a possible owner of a clustered BizTalk host, the cluster resource for the host instance is taken offline in Windows Cluster. If you need to unconfigure a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer that is listed as a possible owner of a clustered BizTalk host without taking the cluster resource for the host instance offline, follow these steps:  
  
  - In the Windows Server Failover Cluster Management interface, fail over the clustered host to a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer other than the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer that you will unconfigure.  
  
  - In the BizTalk Server Administration console, select the instance of the clustered BizTalk host that corresponds to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer which is to be unconfigured.  
  
  - Delete the host instance. If prompted with an error choose the option to forcefully delete the host instance.  
  
  - Unconfigure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
- When a BizTalk host is configured as a clustered host, a corresponding cluster resource is created in the specified cluster resource group on the cluster.  
  
   By default, a clustered BizTalk host resource is configured with the following restart values on a Windows Server failover cluster which are available on the **Policies** tab of the **Properties** dialog box for the cluster resource:  
  
  |Option|Value|  
  |------------|-----------|  
  |If resource fails, attempt restart on current node.|**True** <br />The Cluster service will attempt to restart the resource if it fails.|  
  |Period for restarts (mm:ss):|**15:00** <br />Specifies the time period during which restart attempts are counted.|  
  |Maximum restarts in the specified period:|**1** <br />Specifies the maximum number of restart attempts allowed during the **Period for restarts (mm:ss)** .|  
  |If restart is unsuccessful, fail over all resources in this service or application.|**True** <br />The Cluster service will attempt to restart the resource by failing over the entire resource group to another cluster node.|  
  |If all the restart attempts fail, begin restarting again after the specified period (hh:mm):|**1:00** <br />Specifies an extended waiting period after which the Cluster service will begin another series of restart attempts.|  
  |Pending timeout (mm:ss):|**3:00** <br />Specifies the length of time the resource can take to change states between Online and Offline before the Cluster service puts the resource in the Failed state.|  
  
   The default restart values dictate that the Windows Server failover cluster will attempt to restart a failed instance of a clustered BizTalk host instance up to 1 time within a time span of 15 minutes. Since the **If restart is unsuccessful, fail over all resources in this service or application** value is set to **True**, any restart attempts will also fail over the cluster resource group to another cluster node. If a failed instance of a clustered BizTalk host cannot be restarted in the specified number of attempts during the specified time period then the clustered BizTalk host will assume a state of **Failed** in the Failover Cluster Management interface. If a clustered BizTalk host assumes a state of **Failed** then it must be manually started in the Failover Cluster Management.  
  
   By default, a clustered BizTalk host resource is configured with the following restart values on a server cluster which are available on the **Advanced** tab of the **Properties** dialog box for the cluster resource:  
  
  |**Option**|**Value**|  
  |----------------|---------------|  
  |Restart|**True**<br /><br /> The Cluster service will attempt to restart the resource if it fails.|  
  |Affect the group|**True**<br /><br /> The Cluster service will attempt to restart the resource by failing over the entire resource group to another cluster node.|  
  |Restart Threshold|**3**<br /><br /> Specifies the maximum number of restart attempts allowed during the **Restart Period**. If the number of restart attempts exceeds the **Restart Threshold** during the **Restart Period** then the cluster resource assumes a state of **Failed** and the Cluster service does not attempt any more restarts.|  
  |Restart Period|**900 seconds**<br /><br /> Specifies the time period during which restart attempts are counted. The **Restart Period** is initialized upon the first restart attempt. The restart attempt count is reset to zero if the **Restart Threshold** is not exceeded for the duration of the **Restart Period**.|  
  
   The default restart values dictate that Windows Server cluster will attempt to restart a failed instance of a clustered BizTalk host instance up to 3 times within a time span of 900 seconds. Since the **Affect the group** value is set to **True**, any restart attempts will also fail over the cluster resource group to another cluster node. If a failed instance of a clustered BizTalk host cannot be restarted in the specified number of attempts during the specified time period, then the clustered BizTalk host will assume a state of **Failed** in Cluster Administrator. If a clustered BizTalk host assumes a state of **Failed**, then it must be manually started in Cluster Administrator.  
  
## Procedures  
  
#### To configure a BizTalk host as a cluster resource  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click to expand **BizTalk Server Administration**, click to expand **BizTalk Group [\<servername\>:\<management database\>]**, click to expand **Platform Settings**, and then click to expand **Hosts**. The list of hosts appears under the folder.  
  
2. Right-click the host that you would like to cluster, and then select **Cluster**.  
  
   > [!NOTE]
   >  Ensure that you have created an instance of the host on all member nodes that are possible owners of a cluster group before adding the BizTalk host to that cluster group.  
  
3. Select the cluster group that you would like to run the host in from the drop-down list of available cluster groups.  
  
   > [!NOTE]
   >  As soon as a host is clustered, it is brought online and will begin processing documents for any adapter handlers or orchestrations that are configured to run in the host.  
  
#### To uncluster a clustered BizTalk host  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click to expand **BizTalk Server Administration**, click to expand **BizTalk Group [\<servername\>:\<management database\>]**, click to expand **Platform Settings**, and then click to expand **Hosts**. The list of hosts appears under the folder.  
  
2. Right-click the clustered host that you would like to uncluster, and then select **Uncluster**.  
  
   > [!NOTE]
   >  When a clustered host is unclustered, any host instances associated with the clustered host are stopped and the host will stop processing documents for any adapter handlers or orchestrations that are configured to run in the host.