---
description: "Learn more about: How to Configure SSO in a Multicomputer Scenario"
title: "How to Configure SSO in a Multicomputer Scenario"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure SSO in a Multicomputer Scenario
This section contains instructions for configuring Enterprise Single Sign-On (SSO) in a three-computer scenario.  
  
 In the following scenario, computer A is the master secret server, computer B is the Single Sign-On server, and computer C holds the SSO database. Computer B can act as a runtime server, as an administration server (administration sub services of SSO use this server for managing the SSO database), or as a mapping server (administration and client sub services of SSO use this server to manage mappings).  
  
 If you want to add more SSO servers to your environment, follow the steps for configuring computer B. Any new SSO servers will point to the existing SSO database, and cannot be the master secret server.  
  
> [!NOTE]
>  It is recommended that you configure the master secret server on a different computer from the Single Sign-On server and the SSO database.  
  
### To configure the master secret server and create the SSO database on Computer A  
  
1.  Perform a custom installation of BizTalk Server, and install only the Enterprise Single Sign-On Master Secret Server component.  
  
2.  Run the Configuration Wizard to configure SSO on the master secret server. On the **Configuration Questions** page, select the option to **Create a new SSO system**.  
  
3.  On the **Windows Accounts** page, specify the service account credentials for the SSO service. This must be a member of the SSO Administrators group.  
  
4.  On the **Database Configurations** page, specify the location of the SQL Server (computer C) and the name of the SSO database (SSODB).  
  
5.  Specify the options to back up the Master Secret.  
  
6.  Complete the configuration.  
  
### To configure the SSO server on Computer B  
  
1.  Install Enterprise Single Sign-On on Computer B.  
  
    > [!NOTE]
    >  This can be a BizTalk Server or Host Integration Server computer, a Web server, or an SSO-only server (SSO runtime components).  
  
2.  Run the Configuration Wizard to configure SSO. On the **Configuration Questions** page, select the option to **Join an existing SSO system**.  
  
3.  On the **Windows Accounts** page, specify the service account credentials for the SSO service. This must be a member of the SSO Administrators group.  
  
4.  On the **Database Configurations** page, point to the location of the SQL Server (computer C) and the name of the SSO database (SSODB).  
  
## See Also  
 [How to Cluster the Master Secret Server](../core/how-to-cluster-the-master-secret-server1.md)   
 [Installing SSO](../core/installing-sso.md)
