---
title: "How to Cluster the Master Secret Server | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 011e4b8a-27c8-44a7-85a5-f99e81877ec1
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Cluster the Master Secret Server
It is strongly recommended that you follow the instructions in this section to cluster the Enterprise Single Sign-On (SSO) service on the master secret server successfully.  
  
 Before you start configuring SSO in a cluster environment, it is recommended that you understand how clustering works.
  
 When you cluster the master secret server, the Single Sign-On Servers communicate to the active clustered instance of the master secret server. Similarly, the active clustered instance communicates with the Credential database.  
  
 You must be an SSO administrator to perform this procedure.  
  
> [!CAUTION]
>  You cannot install the master secret server on a Network Load Balancing (NLB) cluster.  
  
### To cluster the master secret server  
  
1.  Perform a custom installation to install the master secret server on the first node of the cluster (for example, ClusterNode1).  
  
2.  In the **Configuration Wizard**, on the **Configuration Questions** page, in the **Is this the master secret server?** list, select **Yes**, and then click **Next**.  
  
3.  Specify the service account credentials for SSO service. This must be a member of the SSO Administrators group account.  
  
4.  Specify the location of the SQL Server and SSO Credential database (SSODB).  
  
5.  Back up the master secret on the active node.  
  
6.  Perform a custom installation to install the master secret server on the second node of the cluster (ClusterNode2).  
  
7.  Use the **Configuration Wizard** to configure an Enterprise SSO Server on the second node of the cluster. This time, however, select **No** when you reach the question in step 2, because this is not the initial installation of the master secret server.  
  
8.  Click **Next**, and then complete the **Configuration Wizard**.  
  
9. Stop the SSO service by typing `net stop entsso` at the command line.  
  
10. Change the master secret server name in the SSO Credential database to the cluster name. For example, if the cluster is named MSS_CLUSTER, change the name from ClusterNode1 to MSS_CLUSTER.  
  
11. Use a text editor to copy and paste the following code into an .xml file (for example: MSS CLUSTER.xml) and save the file:  
  
    ```  
    <sso>  
      <globalInfo>  
         <secretServer>MSS_CLUSTER</secretServer>  
    </globalInfo>  
       </sso>  
    ```  
  
12. At the command line, navigate to the Enterprise Single Sign-On installation directory. The default is Program Files\Common Files\Enterprise Single Sign-On.  
  
13. Type `ssomanage -updatedb <filename>` where *filename* is the name of the .xml file in the previous step. This updates the master secret server name in the database.  
  
     Ignore any run-time errors. The Microsoft Distributed Transaction Coordinator (DTC) was not configured to run on a cluster, and may be unable to start.  
  
14. Open a command prompt on master secret server 1 and type `comclust -a`.  
  
15. From the **Services** console, right-click **Distributed Transaction Coordinator**, and then click **Restart**.  
  
16. Open a command line on master secret server 2 and type `comclust -a`.  
  
17. From the **Services** console, right-click **Distributed Transaction Coordinator**, and then click **Restart**.  
  
18. Open **Cluster Administrator**, and then click the cluster group that has the master secret server cluster.  
  
19. On the **File** menu, point to **New**, and then click **Resource**.  
  
     The New Resource window opens.  
  
     Under **Name**, type the name of the SSO resource (for example, `ENTSSO`).  
  
     Under **Resource Type**, select **Generic Service**.  
  
20. In the **Possible Owners** window, include each cluster node as a possible owner of the ENTSSO resource.  
  
21. After you create the **ENTSSO** resource, right-click **ENTSSO**, and click **Properties**.  
  
22. In the **Cluster Properties** dialog box, click the **Security** tab, and verify that the user under which the application is running has sufficient user rights (not a local administrator) to access the cluster.  
  
23. Open **Cluster Administrator**, right-click the cluster group that has the master secret server cluster, and then click **Move group**.  
  
     This moves the master secret server resources from the first node to the second node.  
  
24. Click **Start**, click **Run**, and then type `cmd`.  
  
25. At the command prompt, navigate to the Enterprise Single Sign-On installation directory. The default is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
26. Type `ssoconfig -restoresecret <restore file>`, where \<*restore file*> is the path and name of the back-up file that contains the master secret.  
  
## See Also  
 [Master Secret Server](../esso/master-secret-server.md)   
 [Installing Enterprise Single Sign-On](../esso/installing-enterprise-single-sign-on.md)   
 [High-Availability Installation Options](../esso/high-availability-installation-options.md)