---
title: "How to Configure Enterprise Single Sign-On in a Multicomputer Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6eb9066c-a35f-4399-b066-903c3b07e614
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Configure Enterprise Single Sign-On in a Multicomputer Scenario
This section contains instructions for configuring Enterprise Single Sign-On (SSO) in a three-computer scenario.  
  
 In the following scenario, computer A is the master secret server, computer B is the Single Sign-On server, and computer C holds the Credential database. Computer B can act as a runtime server, as an administration server (administration sub services of SSO use this server for managing the Credential database), or as a mapping server (administration and client sub services of SSO use this server to manage mappings).  
  
 If you want to add more SSO servers to your environment, follow the steps for configuring computer B. Any new SSO servers will point to the existing Credential database, and cannot be the master secret server.  
  
> [!NOTE]
>  It is recommended that you configure the master secret server on a different computer from the Single Sign-On server and the Credential database.  
  
### To configure the master secret server and create the Credential database on Computer A  
  
1. Perform a custom installation of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)], and install only the Enterprise Single Sign-On runtime component.  
  
2. Run the Configuration Wizard to configure SSO on the master secret server.  
  
    On the **Configuration Questions** page, in the **Is this the master secret server** list, select **Yes**, and then click **Next**.  
  
3. On the **Windows Accounts** page, specify the service account credentials for the SSO service. This must be a member of the SSO Administrators group.  
  
4. On the **Database Configurations** page, specify the location of the SQL server (computer C) and the name of the Credential database (SSODB).  
  
5. Back up the master secret.  
  
    For more information, see [How to Back Up the Master Secret](../esso/how-to-back-up-the-master-secret.md).  
  
### To configure the SSO server on Computer B  
  
1.  Install Enterprise Single Sign-On on Computer B.  
  
    > [!NOTE]
    >  This can be a Host Integration Server computer, or an SSO-only server (SSO runtime components).  
  
2.  Run the Configuration Wizard to configure SSO.  
  
     On the **Configuration Questions** page, in the **Is this the master secret server** list, select **No**, and then click **Next**.  
  
3.  On the **Windows Accounts** page, specify the service account credentials for the SSO service. This must be a member of the SSO Administrators group.  
  
4.  On the **Database Configurations** page, point to the location of the SQL server (computer C) and the name of the Credential database (SSODB).  
  
## See Also  
 [How to Cluster the Master Secret Server](../esso/how-to-cluster-the-master-secret-server.md)   
 [Installing Enterprise Single Sign-On](../esso/installing-enterprise-single-sign-on.md)   
 [High-Availability Installation Options](../esso/high-availability-installation-options.md)