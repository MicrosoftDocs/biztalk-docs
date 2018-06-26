---
title: "SSO Security Recommendations | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8132964f-3401-47c6-b98a-b842c5e6790f
caps.latest.revision: 7
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SSO Security Recommendations
This section contains recommendations for how to help secure your Enterprise Single Sign-On (SSO) system.  
  
 With the Enterprise Single Sign-On (SSO) system, users can connect to different systems by using only one set of credentials. Host Integration Server uses the SSO system as a store for sensitive information. Although it automatically installs whenever you install the Host Integration Server runtime, you can also install Enterprise Single Sign-On as a stand-alone component, independent of your Host Integration Server environment. We recommend you follow these guidelines for securing and deploying the Enterprise SSO services and resources in your environment.  
  
## General Deployment Recommendations for SSO  
  
-   You must have a time server in your environment to ensure all SSO servers are synchronized. If the clocks on the SSO servers are not synchronized, this could compromise the security of your environment.  
  
-   Considering there is only one master secret server in your entire environment, we you use an active-passive cluster configuration for the master secret server. For more information about clustering the master secret server, see [How to Cluster the Master Secret Server](../esso/how-to-cluster-the-master-secret-server.md).  
  
-   The master secret server holds the encryption key the SSO system uses to encrypt the information in the SSO database. We recommend that you do not install or configure any other products or services on this computer.  
  
    > [!NOTE]
    >  The computer where you install and configure the master secret server does not have to be a server.  
  
-   The master secret server should have access to a removable media or NTFS file system folder in order to back up and restore the master secret. If you use removable media, ensure that you take appropriate measures to protect the removable media. If you back up the master secret to an NTFS file system, ensure that you protect the file and the folder. Only the SSO Administrator should have access to this file.  
  
-   You should back up the master secret as soon as the master secret server generates it. This is so that you can recover the data in the SSO database in the event the master secret server fails. For more information about backing up the master secret, see [Managing the Master Secret](../esso/managing-the-master-secret.md).  
  
-   Back up your current secret, or generate a new secret regularly, for example, once a month. Without the secret, you cannot retrieve information from the SSO database. For more information about backing up and restoring the master secret, see [Managing the Master Secret](../esso/managing-the-master-secret.md).  
  
## Security Recommendations for SSO Groups and Accounts  
  
-   We recommend that you use Windows groups, and not single user accounts, especially for the SSO Administrator and SSO Affiliate Administrator groups. These groups must have at least two user accounts as members of the group at all times.  
  
-   The SSO runtime service accounts and the SSO administrator user accounts should be different accounts, even when they are members of the same SSO Administrators group. The SSO Administrator users who perform administrative tasks such as generating and backing up the secret must be Windows administrators, whereas the SSO runtime service accounts do not need to be Windows administrators.  
  
    > [!IMPORTANT]
    >  Windows administrator user rights do not supersede the user rights of the SSO administrator. To perform any SSO administration-level task, you must be a member of SSO Administrators group even if you already are a Windows administrator.  
  
-   If you use the SSO ticketing feature, you must use domain accounts that the computers in the processing domain (domain where the SSO servers are) recognize.  
  
-   We recommend you use a unique service account for the SSO service corresponding to the master secret server.  
  
-   The SSO Administrator account is a highly privileged account in the SSO system, which is also the SQL Server administrator account for the SQL server that has the SSO database. You should have dedicated accounts for SSO administrators, and should not use these accounts for any other purposes. You should limit the membership to the SSO Administrators group only to those accounts responsible for running and maintaining the SSO system.  
  
## Security Recommendations for an SSO Deployment  
  
-   If your network supports Kerberos authentication, you should register all SSO servers. When you use Kerberos authentication between the master secret server and the SSO database, you must configure Service Principal Names (SPN) on the SQL server where the SSO database is located.
  
-   When you are running Windows Server 2003, if the master secret server is on a different domain from the other SSO servers and from the SSO database, you must disable RPC security (as used for Data Transaction Coordinator (DTC) authentication between computers) on the master secret server, on the SSO servers (processing computers in the processing domain), and on the SSO database. RPC security is a new DTC feature in Windows Server 2003. When you disable RPC security, the DTC authentication security level for RPC calls goes back to one available in Microsoft Windows. For more information about disabling RPC security, see the Microsoft Help and Support Web site at http://go.microsoft.com/fwlink/?LinkId=24774.  
  
-   SSO administrators should regularly monitor the event log in the master secret server and the SSO server for SSO auditing events.  
  
-   In addition to firewalls, we recommend you use Internet Protocol security (IPsec) or Secure Sockets Layer (SSL) between all the SSO servers and the SSO database. For more information about SSL, see the Microsoft Help and Support Web site at http://go.microsoft.com/fwlink/?LinkId=16731.  
  
## Perimeter Network  
 When running Internet Information Services (IIS) and Enterprise Single Sign-On, follow these recommendations:  
  
-   If IIS is in a perimeter network (also known as a screened subnet), provide another server running IIS behind the firewall to connect to the SSO system.  
  
-   Do not open the remote procedure calls (RPC) port on IIS.  
  
## SQL Server Access  
 All SSO servers access the SQL Server Credential database. 
  
 We recommend you use Secure Sockets Layer (SSL) and/or Internet Protocol security (IPsec) to help secure the transmission of data between the SSO servers and the Credential database. For more information about using SSL, see [http://go.microsoft.com/fwlink/?LinkId=33176](http://go.microsoft.com/fwlink/?LinkId=33176).  
  
 To enable SSL for only the connection between the SSO server and the Credential database, you can set SSL support on every SSO server using the ssoconfig utility. This option enables SSO to always use SSL when accessing the Credential database. For more information, see [How to Enable SSL for Enterprise Single Sign-On](../esso/how-to-enable-ssl-for-enterprise-single-sign-on.md).  
  
## Strong Passwords  
 It is very important that you use strong passwords for all accounts, especially the accounts that are members of the SSO Administrators group, because these users have control over the entire SSO system.  
  
## SSO Administrator Accounts  
 We recommend that you use different service accounts for the SSO services running on different computers. You should not use the SSO administrator account that performs administration operations such as generating and backing up the secret for the SSO service. Although the SSO service accounts should not be local administrators on that computer, the SSO administrator who is performing administration operations must be a local administrator on the computer for some operations.  
  
## Master Secret Server  
 We highly recommend that you secure and lock down the master secret server. You should not use this server as a processing server. The only purpose of this server should be to hold the master secret. You should ensure the physical security of this computer and only SSO Administrators should have access to this computer.  
  
## Kerberos  
 SSO supports Kerberos, and we recommend that you set up Kerberos for SSO. To set up Kerberos with SSO, you must register a Secure Principal Name (SPN) for the SSO service. By default, when you set up Kerberos, SSO uses that SPN to authenticate the components using the SSO Service. We recommend you set up Kerberos authentication between the SSO administrative sub services and the SSO server. You can also user Kerberos authentication between the SSO servers and between the SSO servers and the SQL Server where the Credential database is.  
  
 To set up and verify Kerberos, you use the utilities **setspn** and **kerbtray**. For more information about these utilities, see [http://go.microsoft.com/fwlink/?LinkId=33178](http://go.microsoft.com/fwlink/?LinkId=33178) and [http://go.microsoft.com/fwlink/?LinkId=33179](http://go.microsoft.com/fwlink/?LinkId=33179).  
  
## Delegation  
 When you are using Windows Server 2003, you can use constrained delegation, but we recommend that you do not use delegation to perform the tasks of the Single Sign-On administrator. Similarly, we recommend you do not delegate additional tasks or user rights to the Single Sign-On administrator.  
  
## Auditing  
 Auditing is a critical mechanism for tracking information in your environment. Enterprise Single Sign-On (SSO) audits all operations performed in the Credential database. SSO uses event logs and audit logs of the database itself. SSO provides two audit levels for the Single Sign-On servers:  
  
- Positive auditing levels audit successful operations.  
  
- Negative auditing levels audit operations that fail.  
  
  SSO administrators can set the positive and negative audit levels that suit their corporate policies.  
  
  You can set positive and negative audits to one of the following levels:  
  
- 0 = None - This level issues no audit messages.  
  
- 1 = Low  
  
- 2 = Medium  
  
- 3 = High - This level issues as many audit messages as possible.  
  
  The default value for positive auditing is 0 (none), and the default value for negative auditing is 1(low). You may want to change these values depending on the level of auditing you want for your SSO system.  
  
> [!IMPORTANT]
>  Enterprise Single Sign-On auditing issues messages that are generated by the Single Sign-On service. This is not a security audit, and the SSO system does not save the information in the Security log of the Event Log. The SSO system saves the SSO audit messages directly to the Application Event Log.  
  
## Database-Level Auditing  
 For database-level auditing, the SSO system tracks the operations performed on the Credential database in the audit tables in the database. The size of these audit tables are defined at the SSO system level. You can audit for affiliate applications that are deleted, for mappings that are deleted, and for credential look-ups that are performed. By default, the audit size is set to 1000 entries. SSO administrators can change this size to meet their corporate policies.  
  
## Using Enterprise Single Sign-On Accounts  
 This section contains best practices when you are using domain and local groups and individual accounts in the Enterprise Single Sign-On (SSO) system.  
  
### Domain Windows Groups and Accounts  
 When you are working with domain Windows groups, the following recommendations apply:  
  
-   Use domain groups and domain accounts.  
  
-   Use a domain group for SSO administrators. You should not specify an individual domain account as the SSO administrator, because you cannot change this account from one individual account to another individual account.  
  
-   Although you can specify an individual domain account as the SSO affiliate administrator, you should use a domain group.  
  
-   Although you can specify an individual domain account as the application administrator, you should use a domain group.  
  
-   You must use domain groups for the application users account. The SSO applications users account does not support an individual account.  
  
## See Also  
 [How to Audit Enterprise Single Sign-On](../esso/how-to-audit-enterprise-single-sign-on.md)   
 [How to Update the Credential Database](../esso/how-to-update-the-credential-database.md)