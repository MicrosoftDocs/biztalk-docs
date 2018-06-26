---
title: "Maintaining Reliability | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09cdce13-a75b-44d7-8388-7a868bb51c69
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Maintaining Reliability
This section provides information about how you can resolve reliability issues with a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system. These issues may be discovered by the routine maintenance checks that are performed in the [Routine Maintenance Checklists](../technical-guides/routine-maintenance-checklists.md) section of this document.  

 In addition to the topics in this section, other topics in this document address reliability issues. These topics are listed in [Related Sections](../technical-guides/maintaining-reliability.md#BKMK_Related) below.  

## Testing Group Failover  
 Perform the procedures in this section as part of the reliability checks that should be performed monthly. These procedures include testing the group failover policy, and testing whether the group resources can fail over.  

> [!NOTE]  
>  If the computer is joined to a domain, members of the Domain Admins group should be able to perform this procedure.  

> [!NOTE]  
>  To perform the procedures in this section, you must be logged on as a member of the Administrators group on the local computer, or you must have been delegated the appropriate authority.  

 Perform the following steps to test group failover on computers running Windows Server 2008.  

#### To test a group failover policy  

1.  Make sure you have installed the **Failover Clustering** feature on at least two computer running Windows Server 2008 so as to create a two node Windows Failover Cluster. For instructions on how to install this feature, see [Install the Failover Clustering Feature](http://go.microsoft.com/fwlink/?LinkId=157259) (http://go.microsoft.com/fwlink/?LinkId=157259).  

2.  Open Failover Cluster Management by clicking **Start**, clicking **Administrative Tools**, and then clicking **Failover Cluster Management**.  

3.  In the console tree, expand the cluster node, expand the **Services and Applications** node, right-click the clustered instance of the application to be failed over, and then click **Properties**.  

4.  On the **Failover** tab, set **Maximum failures in the specified period** to 0, and then click **OK**.  

5.  In the console tree, expand the **Services and Applications** node.  

6.  In the details pane, right-click a resource, and then click **Properties**.  

7.  On the **Policies** tab, set **Maximum restarts in the specified period** to 0, and then click **OK**.  

8.  Right-click the resource, click **More Actions**, and then click **Simulate Failure of this resource**. Verify whether the group reacts based on the policy you specified in the previous step.  

9. Right-click the clustered instance of the application to be failed over, and then click **Properties**.  

10. On the **Failover** tab, set **Maximum failures in the specified period** to 1, and then click **OK**.  

11. Right-click the resource and select **Bring this resource online**.  

#### To test whether group resources can fail over  

1.  Make sure you have installed the **Failover Clustering** feature on the computer running Windows Server 2008. For instructions on how to install this feature, see [Install the Failover Clustering Feature](http://go.microsoft.com/fwlink/?LinkId=157259) (http://go.microsoft.com/fwlink/?LinkId=157259).  

2.  Open Failover Cluster Management by clicking **Start**, clicking **Administrative Tools**, and then clicking **Failover Cluster Management**.  

3.  In the console tree, expand the cluster node, expand the **Services and Applications** node, and then click the clustered instance of the application to be failed over.  

4.  On the **Action** menu, click **Move this service or application to another node**, and then click the node to which the application will be failed over.  

5.  In the **Please confirm action** dialog box, choose to move the application to selected node.  

6.  Make sure that the node to which you moved the application to is listed against the **Current Owner** in the details pane of the application.  

##  <a name="BKMK_BTSGrp"></a> Ensuring Multiple Servers Are Part of a BizTalk Group  
 To ensure the reliability of a system, at least two physical BizTalk servers should be part of the BizTalk group.  If you need to add a server to a BizTalk group, keep the following in mind:  

- A server can only be associated with one BizTalk group. If a server already belongs to another group, you must first remove that server from its current group before you can add it to a new group. For more information about removing a server from a BizTalk group, see "How to Remove a Server from a Group" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=155577](http://go.microsoft.com/fwlink/?LinkId=155577).  

- BizTalk groups associated with different servers in a BizTalk Server environment do not interact except to exchange messages.  

- The BizTalk Server runtime must be installed on the computer you want to add to the BizTalk group.  

> [!NOTE]  
>  To perform the procedures in this topic, you must be logged on as a member of the SSO Administrators group and as a member of the Windows Administrators group.  

#### To determine whether at least two physical BizTalk servers are part of the BizTalk group  

1. Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console by clicking **Start**, pointing to **All Programs**, pointing to **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and then clicking **BizTalk Server Administration**.  

2. Expand the [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] node, expand the **BizTalk Group** node, and then expand the **Platform Settings** node.  

3. Click the **Servers** node. Verify that more than one server is listed in the **Servers** pane.  

   > [!NOTE]  
   >  To view information about the server, right-click the server, point to **View**, and then click **Group Hub Page**.  

#### To add a server to a BizTalk group  

1. On the computer that you want to add to a BizTalk group, click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and then click **BizTalk Server Configuration**.  

2. In **Microsoft BizTalk Server 2010 Configuration**, select **Custom configuration**.  

3. In **Database server name**, type the name of the SQL server for the BizTalk group that the server is joining.  

4. In **Service credential**, type the appropriate user name and password that the services will use, and then click **Configure**.  

5. In the navigation tree on the left side of the screen, click **Enterprise SSO**.  

6. On the **Enterprise Single Sign-On** page, click **Join an existing SSO system**.  

   > [!NOTE]  
   >  Ensure that the server name and database name point to the master SSO database server for the BizTalk group that the server is joining.  

7. In the navigation tree on the left side of the screen, click **Group**.  

8. On the **Group** page, click **Join an existing BizTalk Group**.  

   > [!NOTE]  
   >  Ensure that the server name and database name point to the databases for the BizTalk group that the server is joining.  

9. On the menu bar, click **Apply Configuration** to configure both Enterprise Single Sign-On and the group on this computer.  

##  <a name="BKMK_Related"></a> Related Sections  

- For information about checking for failed disks in the hardware RAID, see "View Disk Properties" in the Windows Server 2003 product Help at [http://go.microsoft.com/fwlink/?linkid=104161](http://go.microsoft.com/fwlink/?linkid=104161).  

- For information about manually checking for suspended messages, see "Investigating Orchestration, Port, and Message Failures" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkID=154512](http://go.microsoft.com/fwlink/?LinkID=154512).  

- For information about ensuring that each host has an instance running on at least two physical BizTalk servers, see [High Availability for BizTalk Hosts](../technical-guides/high-availability-for-biztalk-hosts.md).  

- For information about ensuring that each host has an instance running on at least two physical BizTalk servers, see [Scaling Out Receiving Hosts](../technical-guides/scaling-out-receiving-hosts.md).  

- For information about ensuring that failover for all clustered services has been tested, see [Clustering the Master Secret Server](../technical-guides/clustering-the-master-secret-server.md).  

- For information about ensuring that the BizTalk databases are clustered under SQL Services, see [Clustering the BizTalk Server Databases2](../technical-guides/clustering-the-biztalk-server-databases2.md).  

- For information about determining whether any unstable code is being used (requiring separate hosts), see [High Availability for BizTalk Hosts](../technical-guides/high-availability-for-biztalk-hosts.md).  

- For information about performing functional testing of all new BizTalk applications, see [Testing an Application](../technical-guides/testing-an-application.md)
