---
description: "Learn more about: Security Recommendations for a BizTalk Server Deployment"
title: "Security Recommendations for a BizTalk Server Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "deploying, security"
  - "Windows Server 2003 Security Configuration Wizard (SCW)"
  - "user accounts, security"
  - "permissions"
  - "access control"
  - "security, deploying"
  - "channel level encryption"
  - "security, permissions"
ms.assetid: 033fff11-d989-46ba-83ed-5063f7cd7818
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Security Recommendations for a BizTalk Server Deployment
This section contains high-level, feature-agnostic recommendations to secure your Microsoft BizTalk Server environment.

## Topology-level recommendations
 **Use channel level encryption.** By default, network data flows between various components within BizTalk Server are in clear text. When sniffing or tampering of data as messages travel from one computer to another is a concern, we recommend using channel-level encryption, such as Internet Protocol security (IPSec) or Secure Sockets Layer (SSL). While BizTalk Server does not configure channel-level encryption by default, BizTalk Server does not put critical data such as encryption keys and passwords on the wire in clear text. The SSO database manages sensitive information by storing it in encrypted form by using the master secret (encryption key) provided by the master secret server. By default, the SSO database receives, stores, and sends sensitive information in encrypted form.

 For more information about SSL, see [https://go.microsoft.com/fwlink/p/?LinkId=189708](https://go.microsoft.com/fwlink/p/?LinkId=189708).

 **Help ensure the physical security of the servers.** You must also take into consideration the physical security of the servers, devices, networks, cables, power supply, and other components. You should place your computers in a safe environment, and limit access to the computers that contain business-critical information, such as the databases.

 **Only install the components you will use.** If you need to install Internet Information Services (IIS) in your environment (on the computers in the perimeter network, or in the computers running the HTTP and SOAP adapters), you do not need to install the File Transport Protocol (FTP), WebDAV and Simple Mail Transfer Protocol (SMTP) sub-components of IIS. Similarly, ensure you only install and configure the BizTalk Server features you need for your environment. For example, only configure the BizTalk Message Queuing adapter if you use it. This helps you reduce the potential attack surface in your environment.

If using Internet Explorer, we recommend you turn on the enhanced security of Internet Explorer.

 **Install service packs and updates**. We recommend always installing the latest product service packs and Microsoft updates on all servers that have [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] resources, including [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)].

 **Do not save passwords in clear-text in scripts or binding files.** You should save scripts in locations with strong discretionary access control lists (DACLs) so that only the BizTalk Server administrators have permissions to view, modify and run these scripts. When the scripts and binding files require passwords, ensure you mask the passwords as soon as you use the scripts for configuration or deployment. Do not leave passwords in these files in clear text.

 **Use strong discretionary access controls lists (DACLs).** Ensure that you only give access to a resource to the users and accounts that use it, and that you give them the least permissions possible to perform their task. Place configuration scripts in locations with DACLs to the BizTalk Server administrator and do not put clear text passwords in the scripts. Ensure the temporary directories for all the service accounts BizTalk Server uses have DACLs, so that only that service account and BizTalk administrators have access to it.

 When you have custom adapters, we recommend that you store the adapter extension components in a location with strong DACLs, so only BizTalk Server administrators have write permissions to these components.

 **Do not place BizTalk Servers in the perimeter network.** Regardless of the size of your company, placing BizTalk Server in the perimeter network exposes the servers to both direct attacks from the Internet and to attacks from other servers in the perimeter network that may be compromised. Because BizTalk Server communicates to Microsoft SQL Server databases in the Data domain, a malicious user could leverage a compromised BizTalk Server to tamper with critical business processing and configuration data.

## BizTalk Server groups and accounts
 **Use accounts with minimum permissions and user rights.** All accounts in the BizTalk Server system should have the minimum user rights they need to perform their tasks. For example, the service accounts that you use in the processing servers should not have administrative user rights in the BizTalk Server, SQL Server, or Windows Server. For more information about the minimum security permissions and user rights an account needs to perform a task in BizTalk Server, see [Minimum Security User Rights](../core/minimum-security-user-rights.md). For more information about the groups and accounts that BizTalk Server uses, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).

 **Use different accounts for different functions.** To help preserve the security of your BizTalk Server environment, we recommend that you create different service accounts for each of the host instances running in your environment. This also allocates for better availability during password updates. We recommend that one service account is not a member of multiple Windows groups for BizTalk Server.

 In addition, we recommend that you use different Windows groups for each BizTalk Host, and that the service accounts that are members of one group not be members of the Windows group for another host. This provides strong security isolation for each BizTalk Host.

 We recommend that you create a Windows group just for the tracking host, and that you use a service account in this group for the tracking host instance. Do not use this service account for any other services, and do not use a BizTalk administrator account for the tracking host instance.

 **Use different hosts for different functions.** We recommend creating a host solely for tracking. Hosts configured to "host tracking" have read and write access to the tracking tables in the MessageBox database, as well as access to the tables in the Tracking database. Therefore, any objects running in a host that hosts tracking also have access permissions to read and write to these tables. To block access to potentially sensitive tracking data from user items such as pipelines and orchestrations, we recommend that you create a dedicated host for tracking that does not process, send or receives messages.

 In addition, we recommend you use different hosts for processing, receiving, and sending messages. You can then isolate the service accounts that need access to the private certificates for your company. The less code you have running under these accounts, the lower the potential to compromise the accounts through vulnerabilities, which in turn decreases the risk of compromising the private certificates.

 **Change passwords periodically.** You must change the password for the service accounts periodically. Considering you may have multiple service accounts for your host instances, you must change the password for each of these service accounts.

> [!CAUTION]
>  You must change the passwords for the service account for a host instance in the BizTalk Administration Console. Changing the password for the service account for a host instance in the Computer Management console can cause configuration problems.

 **Limit membership to the BizTalk Administrators group.** BizTalk Server administrators have user rights that span across the BizTalk Server environment, including access to most data, encrypted or otherwise. Therefore, an improper configuration resulting from a mistake by a BizTalk administrator can expose critical security holes. A misbehaving BizTalk administrator can do unlimited damage to the system, including a complete compromise of the confidentiality, integrity, and availability of customer data.

 In situations where developers directly deploy orchestrations to computers in the production environment, domain administrators must grant developers BizTalk administrator user rights. This is not recommended for the reason stated earlier.

 **Limit membership to the COM+ Administrators group.** Due to various architectural reasons, the COM+ administrator has user rights as administrator in several BizTalk Server components. For all practical purposes, you must assume that a COM+ administrator on a computer is also a BizTalk administrator, and should limit membership to this group in BizTalk production servers.

 **Give users access only to the computers that run the services they need access to.** Not all accounts need permissions to all computers. BizTalk Host instances hold sensitive information in memory. These could be critical data like passwords or business information. A very tight local user policy should be set up on these computers. For example, only grant local logon rights on these computers to individuals that need them to maintain the deployment. This mitigates threats resulting from access to the swap file and crash dumps.

 **Limit permissions of the Power Users group, or remove it.** The default permissions for the Power Users group give members of this group user rights modify computer-wide settings, including BizTalk assemblies registered in the global assembly cache (GAC). Each computer has GAC, which contains the assemblies that one or more applications share. We recommend that you remove the permission to change assemblies from the Power Users group, or that you delete the Power Users group from the production BizTalk Servers.


## See Also
 [Access Control for Groups and Service Accounts](../core/access-control-for-groups-and-service-accounts.md)
 [Access Control for Administrative Roles](../core/access-control-for-administrative-roles.md)
 [Minimum Security User Rights](../core/minimum-security-user-rights.md)
 [Planning for Security](../core/planning-for-security.md)
