---
description: "Learn more about: Deployment Process"
title: "Deployment Process | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1be4a615-e628-43bd-99be-1f8d67842a95
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Deployment Process
The following steps give a high-level overview of secure deployment of Enterprise Single Sign-On (SSO). For detailed procedures on the actions to take in SQL Server, see the SQL Server documentation.  
  
1.  On the SQL Server domain controller, use the **New Trust Wizard** to create a trust with the following properties:  
  
    -   **Name:** ORCH.com  
  
    -   **Direction:** Two-way  
  
    -   **Sides:** This domain only  
  
    -   **Outgoing Trust Authentication Level - Local Domain:** Selective authentication  
  
    -   **Password:** Choose a password  
  
    -   **Confirm Outgoing Trust:** Yes  
  
    -   **Confirm Incoming Trust:** No  
  
2.  On the ORCH.com domain controller, use the **New Trust Wizard** to create a trust with the following properties:  
  
    -   **Name:** SQL.com  
  
    -   **Direction:** Two-way  
  
    -   **Sides:** This domain only  
  
    -   **Outgoing Trust Authentication Level - Local Domain:** Selective authentication  
  
    -   **Password:** Must be the same as password for ORCH.com  
  
    -   **Confirm Outgoing Trust:** Yes  
  
    -   **Confirm Incoming Trust:** No  
  
3.  On the ORCH.com domain controller, set the domain-wide trust for Incoming from SQL.COM.  
  
4.  On the SQL.com domain controller, set the domain-wide trust for Outgoing from ORCH.COM.  
  
5.  On the ORCH.com domain controller, raise the domain functional level to Windows Server 2003.  
  
6.  In the ORCH domain, create the following new users:  
  
    -   ORCH\SSOSvcUser  
  
    -   ORCH\TestAppUser  
  
    -   ORCH\AffAppUser  
  
7.  Add **Act as part of the operating system** to SSOSvcUser and TestAppUser.  
  
8.  Add **Allowed to Authenticate** privilege to ORCH\TestAdmin.  
  
9. Add ORCH\SSOSvcUser to SQL2 in the SQL domain. This step requires using Advanced View in Active Directory Microsoft Management Console (MMC).  
  
10. On the SQL2 computer, create the following two new logons:  
  
    -   ORCH\TestAdmin  
  
    -   ORCH\SSOSvcUser  
  
11. On the SQL2 domain, create two domain global groups:  
  
    -   ORCH\SSOAdminGroup  
  
    -   ORCH\SSOAffAdminGroup  
  
12. Add **Allowed to Authenticate** privilege to the ORCH\SSOAdminGroup group.  
  
13. On the SQL2 database, create the following new logon:  
  
    -   ORCH\SSOAdminGroup  
  
14. Install the master secret server as follows:  
  
    -   Log onto NTS5 using ORCH\TestAdmin.  
  
    -   Install Enterprise SSO, using SQL2 as the master secret server.  
  
15. Log on to HIS1 using ORCH\TestAdmin, and install Enterprise Single Sign-On. Configure ESSO as SSO join HIS2, using database server name SQL2.  
  
16. Install the Enterprise Single Sign-On Admin utility on HIS3 using ORCH\TestAdmin.  
  
17. Add the following users to the following groups:  
  
    -   Add ORCH\TestAppUser to ORCH\SSOAdminGroup  
  
    -   Add ORCH\AffAppUser to ORCH\TestAffUserGroup  
  
18. Install SQL Server 2000a Enterprise on HIS3, and add logon ORCH\AffAppUser.  
  
19. On the HIS1 machine, open a command prompt and use the following commands to set constrain delegation and protocol transition:  
  
    -   **setspn -A MSSQLSvc/HIS3.ORCH.com:1433 ORCH\SSOSvcUser**  
  
    -   **setspn -A MSSQLSvc/HIS3.ORCH.com:1433 ORCH\TestAppUser**  
  
20. On the **ORCH\SSOSvcUser** and **ORCH\TestAppUser** property pages, set the proper delegation for both user accounts by selecting the following options:  
  
    -   **Trust this user for delegation to specified services only**  
  
    -   **Use any authentication protocol**  
  
21. Using ORCH\TestAdmin on the HIS1 computer, perform the following:  
  
    -   Add ORCH\TestAppUser to Remote Desktop User Group.  
  
    -   Grant **Impersonate after authenticated** privilege to ORCH\SSOSvcUser.  
  
    -   Grant **Impersonate after authenticated** privilege to ORCH\TestAppUser.  
  
22. Verify your deployment by logging on to HIS1 using ORCH\TestAppUser and running the following application configuration:  
  
     Run LogonExternalUser Test.  
  
    ```  
    <SSO>  
       <application name="TestApp">  
          <description>An SSO Test Affiliate Application</description>  
          <contact>AffAppUser@ESSOV2.EBiz.Com</contact>  
          <appUserAccount>ORCH\TestAffAdminGroup</appUserAccount>  
          <appAdminAccount>ORCH\TestAffUserGroup</appAdminAccount>  
          <field ordinal="0" label="User ID" masked="no" />  
          <field ordinal="1" label="Password" masked="yes" />  
          <flags   
             groupApp="no"   
             configStoreApp="no"   
             allowTickets="no"   
             validateTickets="yes"   
             allowLocalGroups="yes"   
             ticketTimeout="yes"   
             adminGroupSame="no"   
             enableApp="yes"   
             hostInitiatedSSO="yes"   
             validatePassword="yes"/>  
       </application>  
    </SSO>  
  
    ```  
  
## See Also  
 [Deployment Overview](../esso/deployment-overview1.md)
