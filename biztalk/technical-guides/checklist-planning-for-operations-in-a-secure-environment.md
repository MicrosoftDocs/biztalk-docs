---
title: "Checklist: Planning for Operations in a Secure Environment | Microsoft Docs"
ms.custom: ""
ms.date: "06/29/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d6464df-6736-46e2-a0c7-cc2a256c5144
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Planning for Operations in a Secure Environment
Running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a secure environment requires additional steps for deployment and configuration. While default operating system installations need not take these into account, but scenarios where restrictive security policies have been applied, you should take into account information in this section. The level of restriction applied onto servers may vary but information below should cover most cases and would be a a good starting point.  

-   [Security Considerations for Computers Running BizTalk Server](../technical-guides/checklist-planning-for-operations-in-a-secure-environment.md#BKMK_BTSSec)  

-   [Security Considerations for Computers Running SQL Server](../technical-guides/checklist-planning-for-operations-in-a-secure-environment.md#BKMK_SQLServSec)  

-   [Additional Security Considerations](../technical-guides/checklist-planning-for-operations-in-a-secure-environment.md#BKMK_AddSec)  

<a name="BKMK_BTSSec"></a>   
## Security Considerations for Computers Running BizTalk Server  
 The following table suggests the security-related settings on computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

### User Rights Assignment  
 To start the User Rights Assignment MMC Snap-in, click **Start**, click **Administrative Tools**, and then click **Local Security Policy**. In the **Local Security Policy** MMC snap-in, expand **Security Settings**, expand **Local Policies**, and then click **User Rights Assignment**.  

|Policy setting|Values|Reference and details|  
|--------------------|------------|---------------------------|  
|Log on as a service|BizTalk Application Users|Required to run BizTalk Host Instances. For more information about different user accounts, see [Windows Groups and User Accounts in BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=155755) (http://go.microsoft.com/fwlink/?LinkID=155755).|  
|Log on as a service|RuleEngine Update Service Account|Required to run RuleEngine Update Service. For more information about different user accounts, see [Windows Groups and User Accounts in BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=155755) (http://go.microsoft.com/fwlink/?LinkID=155755).|  
|Log on as a service|SSO Service Account|Required to run Enterprise Single Sign-On Service. For more information about different user accounts, see [Windows Groups and User Accounts in BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=155755) (http://go.microsoft.com/fwlink/?LinkID=155755).|  

### System Services  
 To start the Services MMC Snap-in, click **Start**, click **Run**, and in the **Run** dialog box, type `services.msc` and press ENTER.  


|                Service name                 | Startup type<sup>1</sup> |                                                              Details                                                               |       User<sup>2</sup>        | Permissions  |             Details             |
|---------------------------------------------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|--------------|---------------------------------|
|           COM+ System Application           |        Automatic         |                                                Required by BizTalk to run properly                                                 |           (default)           |              |                                 |
|                 DHCP Client                 |        Automatic         |                                              Required even if IP addresses are static                                              |           (default)           |              |                                 |
|     Distributed Transaction Coordinator     |        Automatic         |                                                Required by BizTalk to run properly                                                 |      SSO Service Account      | Full Control |  Required to start SSO service  |
|                                             |                          |                                                                                                                                    | BizTalk Hosts Service Account | Full Control | Required to start BizTalk Hosts |
|                                             |                          |                                                                                                                                    |        Network Service        | Full Control |         Required by IIS         |
|            HTTP SSL<sup>3</sup>             |        Automatic         |                                                          Required by IIS                                                           |           (default)           |              |                                 |
|         IPSEC Services<sup>3</sup>          |        Automatic         |                                              IPSEC increases network security if used                                              |           (default)           |              |                                 |
|                  Netlogon                   |        (default)         |                                                                                                                                    |         Local Service         | Full Control |                                 |
| NT LM Security Support Provider<sup>3</sup> |        Automatic         | Required for Kerberos Authentication for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in SQL |           (default)           |              |                                 |
|      Remote Access Connection Manager       |        (default)         |                                                                                                                                    |      SSO Service Account      | Full Control |  Required to start SSO service  |
|                                             |                          |                                                                                                                                    | BizTalk Hosts Service Account | Full Control | Required to start BizTalk Hosts |
|                                             |                          |                                                                                                                                    |        Network Service        | Full Control |         Required by IIS         |
|     Remote Procedure Call (RPC) Locator     |        Automatic         |                                                        Required by BizTalk                                                         |           (default)           |              |                                 |
|  WinHTTP Web Proxy Auto-Discovery Service   |        (default)         |                                                                                                                                    |      SSO Service Account      | Full Control |  Required to start SSO service  |
|                                             |                          |                                                                                                                                    | BizTalk Hosts Service Account | Full Control | Required to start BizTalk Hosts |

 <sup>1</sup> A value of (default) means that the default settings applied by the security policy are not changed  

 <sup>2</sup> A value of (default) means that the default user permissions for the service have not been changed  

### Registry Settings  
 To start the Registry Editor, click **Start**, click **Run**, and in the **Run** dialog box, type `regedit` and press ENTER.  

|Key|User|Permissions|Details|  
|---------|----------|-----------------|-------------|  
|HKLM\ SYSTEM\CurrentControlSet\Services\DHCP|Network Service|Full Control|Required by DHCP Client Service|  
|HKLM\ SYSTEM\CurrentControlSet\Services\TCPIP|Network Service|Full Control|Required by DHCP Client Service|  

<a name="BKMK_SQLServSec"></a>   
## Security Considerations for Computers Running SQL Server  
 The following table suggests the security-related settings on computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  

### User Rights Assignment  
 To start the User Rights Assignment MMC Snap-in, click **Start**, click **Administrative Tools**, and then click **Local Security Policy**. In the **Local Security Policy** MMC snap-in, expand **Security Settings**, expand **Local Policies**, and then click **User Rights Assignment**.  


|                         Policy setting                         |                                             Values                                              |                                                                                                                             Reference and details                                                                                                                             |
|----------------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              Act as part of the operating system               |                  SQL Server Agent Service Account, SQL Server Service Account                   |         Required to run [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information see [Setting Up Windows Service Accounts](http://go.microsoft.com/fwlink/?LinkId=157415) (<http://go.microsoft.com/fwlink/?LinkId=157415>).          |
|               Adjust memory quotas for a process               |                   SQL Server Agent Service Account,SQL Server Service Account                   |         Required to run [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information see [Setting Up Windows Service Accounts](http://go.microsoft.com/fwlink/?LinkId=157415) (<http://go.microsoft.com/fwlink/?LinkId=157415>).          |
|                    Bypass traverse checking                    |                   SQL Server Agent Service Account,SQL Server Service Account                   |         Required to run [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information see [Setting Up Windows Service Accounts](http://go.microsoft.com/fwlink/?LinkId=157415) (<http://go.microsoft.com/fwlink/?LinkId=157415>).          |
|                     Create global objects                      |                                   SQL Server Service Account                                    |                                          Required by SSIS service. For more information see [Setting Up Windows Service Accounts](http://go.microsoft.com/fwlink/?LinkId=157415) (<http://go.microsoft.com/fwlink/?LinkId=157415>).                                           |
| Enable computer and user accounts to be trusted for delegation | SQL Server Service Account, SQL Server Servers, BizTalk Server Servers, SQL Server Cluster Name | Required by BizTalk Server. Server name is in the form \<servername\>$. For more information, see [How to: Enable Kerberos Authentication on a SQL Server Failover Cluster](http://go.microsoft.com/fwlink/?LinkId=157417) (<http://go.microsoft.com/fwlink/?LinkId=157417>). |
|                      Log on as a service                       |                   SQL Server Agent Service Account,SQL Server Service Account                   |         Required to run [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information see [Setting Up Windows Service Accounts](http://go.microsoft.com/fwlink/?LinkId=157415) (<http://go.microsoft.com/fwlink/?LinkId=157415>).          |
|                      Log on as a service                       |                                       SSO Service Account                                       |       Required to run Enterprise Single Sign-On Service. For more information about different user accounts, see [Windows Groups and User Accounts in BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=155755) (<http://go.microsoft.com/fwlink/?LinkID=155755>).       |
|                      Log on as batch job                       |                   SQL Server Agent Service Account,SQL Server Service Account                   |         Required to run [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information see [Setting Up Windows Service Accounts](http://go.microsoft.com/fwlink/?LinkId=157415) (<http://go.microsoft.com/fwlink/?LinkId=157415>).          |
|                 Replace a process level token                  |                   SQL Server Agent Service Account,SQL Server Service Account                   |         Required to run [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information see [Setting Up Windows Service Accounts](http://go.microsoft.com/fwlink/?LinkId=157415) (<http://go.microsoft.com/fwlink/?LinkId=157415>).          |

### System Services  
 To start the Services MMC Snap-in, click **Start**, click **Run**, and in the **Run** dialog box, type `services.msc` and press ENTER.  


|                Service name                 |     Startup type<sup>1</sup>      |                                                              Details                                                               |             User<sup>2</sup>              | Permissions  |            Details            |
|---------------------------------------------|-----------------------------------|------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------|--------------|-------------------------------|
|                 DHCP Client                 |             Automatic             |                                              Required even if IP addresses are static                                              |                 (default)                 |              |                               |
|     Distributed Transaction Coordinator     |              Manual               |                                             Service startup managed by Cluster Service                                             |            SSO Service Account            | Full Control | Required to start SSO service |
|                                             |                                   |                                                                                                                                    |              Network Service              | Full Control |        Required by IIS        |
|            HTTP SSL<sup>3</sup>             |             Automatic             |                                                          Required by IIS                                                           |                 (default)                 |              |                               |
|         IPSEC Services<sup>3</sup>          |             Automatic             |                                              IPSEC increases network security if used                                              |                 (default)                 |              |                               |
|                  Netlogon                   |             (default)             |                                                                                                                                    |               Local Service               | Full Control |                               |
| NT LM Security Support Provider<sup>3</sup> |             Automatic             | Required for Kerberos Authentication for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in SQL |                 (default)                 |              |                               |
|      Remote Access Connection Manager       |             (default)             |                                                                                                                                    |            SSO Service Account            | Full Control | Required to start SSO service |
|                                             |                                   |                                                                                                                                    |              Network Service              | Full Control |        Required by IIS        |
|                   Server                    |             Automatic             |                                              Used for Clustered File Share resources                                               |              Network Service              | Full Control |                               |
|  WinHTTP Web Proxy Auto-Discovery Service   |             (default)             |                                                                                                                                    |            SSO Service Account            | Full Control | Required to start SSO service |
|                                             | World Wide Web Publishing Service |                                                             Automatic                                                              | Required by SQL Server Reporting Services |  (default)   |                               |

 <sup>1</sup> A value of (default) means that the default settings applied by the security policy are not changed  

 <sup>2</sup> A value of (default) means that the default user permissions for the service have not been changed  

### Registry Settings  
 To start the Registry Editor, click **Start**, click **Run**, and in the **Run** dialog box, type `regedit` and press ENTER.  

|Key|User|Permissions|Details|  
|---------|----------|-----------------|-------------|  
|HKLM\ SYSTEM\CurrentControlSet\Services\DHCP|Network Service|Full Control|Required by DHCP Client Service|  
|HKLM\ SYSTEM\CurrentControlSet\Services\TCPIP|Network Service|Full Control|Required by DHCP Client Service|  

<a name="BKMK_AddSec"></a>   
## Additional Security Considerations  
 The following table suggests the other important security-related settings for your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.  


|                                        Affected artifact                                        |                                 Change                                  |                                                                                                               Reference and details                                                                                                                |
|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                       SSO Service Account                                       |       Grant Full Control Permission on Cluster in Cluster Manager       |                                                                                             This change is required for SSO in order to work properly                                                                                              |
| SQL Server Service Account, SQL Server Servers, BizTalk Server Servers, SQL Server Cluster Name |                Trust for Delegation in Active Directory                 | Required for proper Kerberos authentication. For more information, see [How to: Enable Kerberos Authentication on a SQL Server Failover Cluster](http://go.microsoft.com/fwlink/?LinkId=157417) (<http://go.microsoft.com/fwlink/?LinkId=157417>). |
|                                   SQL Server Service Account                                    |                 Grant permission to create SPN Entries                  |            Required for proper Kerberos authentication. For more information, see [How to use Kerberos authentication in SQL Server](http://go.microsoft.com/fwlink/?LinkId=157420) (<http://go.microsoft.com/fwlink/?LinkId=157420>).             |
|                               SQL Server nodes, SQL cluster name                                |         Create SPN entries for user SQL Server Service Account          |            Required for proper Kerberos authentication. For more information, see [How to use Kerberos authentication in SQL Server](http://go.microsoft.com/fwlink/?LinkId=157420) (<http://go.microsoft.com/fwlink/?LinkId=157420>).             |
|                               SQL Network Name  cluster resource                                |     DNS Registration must succeed, Enable  Kerberos Authentication      |                                                                                                    Required for proper Kerberos authentication                                                                                                     |
|                                SQL Server Surface configuration                                 |              Enable Remote Direct Administrator Connection              |                                           Required by SQL Browser Service to function properly which is required by SQL Clients (BizTalk/ASP.NET) in order to correctly locate SQL Server named instance                                           |
|                                 BizTalk Application Users Group                                 | Grant Execute permission on **sp_help_jobhistory** in **msdb** database |                                                                           Required by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                           |

## See Also  
 [Checklists for Other Important Tasks](~/technical-guides/checklists-for-other-important-tasks.md)