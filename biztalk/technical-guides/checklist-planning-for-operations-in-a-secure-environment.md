---
description: "Learn more about: Checklist: Planning for Operations in a Secure Environment"
title: "Checklist: Planning for Operations in a Secure Environment"
ms.custom: ""
ms.date: "06/29/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Checklist: Planning for Operations in a Secure Environment

Running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a secure environment requires additional steps for deployment and configuration. While default operating system installations need not take these into account, but scenarios where restrictive security policies have been applied, you should take into account information in this section. The level of restriction applied onto servers may vary but information below should cover most cases and would be a good starting point.

- [Security Considerations for Computers Running BizTalk Server](#security-considerations-for-computers-running-biztalk-server)

- [Security Considerations for Computers Running SQL Server](#security-considerations-for-computers-running-sql-server)

- [Additional Security Considerations](#additional-security-considerations)

## Security Considerations for Computers Running BizTalk Server

The following information suggests the security-related settings on computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].

### User Rights Assignment
 
To start the User Rights Assignment MMC Snap-in, click **Start**, click **Administrative Tools**, and then click **Local Security Policy**. In the **Local Security Policy** MMC snap-in, expand **Security Settings**, expand **Local Policies**, and then click **User Rights Assignment**.

|Policy setting|Values|Reference and details|
|--------------------|------------|---------------------------|
|Log on as a service|BizTalk Application Users|Required to run BizTalk Host Instances. For more information about different user accounts, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md). |
|Log on as a service|RuleEngine Update Service Account|Required to run RuleEngine Update Service. For more information about different user accounts, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md). |
|Log on as a service|SSO Service Account|Required to run Enterprise Single Sign-On Service. For more information about different user accounts, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md). |

### System Services

To start the Services MMC Snap-in, click **Start**, click **Run**, and in the **Run** dialog box, type `services.msc` and press ENTER.

- **COM+ System Application**:
  - **Startup type** <sup>1</sup>: Automatic
  - **Details**: Required by BizTalk to run properly
  - **User** <sup>2</sup>: (default)

- **DHCP Client**:
  - **Startup type** <sup>1</sup>: Automatic
  - **Details**: Required even if IP addresses are static
  - **User** <sup>2</sup>: (default)

- **Distributed Transaction Coordinator**:
  - **Startup type** <sup>1</sup>: Automatic
  - **Details**: Required by BizTalk to run properly

  The following user accounts need permissions to this service:

  ---
  | User <sup>2</sup>| Permissions | Details |
  | --- |  --- |  --- | 
  | SSO Service Account | Full Control | Required to start SSO service |
  | BizTalk Hosts Service Account | Full Control | Required to start BizTalk Hosts |
  | Network Service | Full Control | Required by IIS |

  ---

- **HTTP SSL** <sup>3</sup>:
  - **Startup type** <sup>1</sup>: Automatic
  - **Details**: Required by IIS
  - **User** <sup>2</sup>: (default)

- **IPSEC Services** <sup>3</sup>:
  - **Startup type** <sup>1</sup>: Automatic
  - **Details**: IPSEC increases network security if used
  - **User** <sup>2</sup>: (default)

- **Netlogon**:
  - **Startup type** <sup>1</sup>: (default)
  - **User** <sup>2</sup>: Local Service
  - **Permissions**: Full Control

- **NT LM Security Support Provider** <sup>3</sup>:
  - **Startup type** <sup>1</sup>: Automatic
  - **Details**: Required for Kerberos Authentication for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in SQL
  - **User** <sup>2</sup>: (default)

- **Remote Access Connection Manager**:
  - **Startup type** <sup>1</sup>: (default)

  The following user accounts need permissions to this service:

  ---
  | User <sup>2</sup>| Permissions | Details |
  | --- |  --- |  --- | 
  | SSO Service Account | Full Control | Required to start SSO service |
  | BizTalk Hosts Service Account | Full Control | Required to start BizTalk Hosts |
  | Network Service | Full Control | Required by IIS |

  ---

- **Remote Procedure Call (RPC) Locator**:
  - **Startup type** <sup>1</sup>: Automatic
  - **Details**: Required by BizTalk
  - **User** <sup>2</sup>: (default)

- **WinHTTP Web Proxy Auto-Discovery Service**:
  - **Startup type** <sup>1</sup>: (default)

  The following user accounts need permissions to this service:

  ---
  | User <sup>2</sup>| Permissions | Details |
  | --- |  --- |  --- | 
  | SSO Service Account | Full Control | Required to start SSO service |
  | BizTalk Hosts Service Account | Full Control | Required to start BizTalk Hosts |

  ---

<sup>1</sup> A value of (default) means that the default settings applied by the security policy are not changed

<sup>2</sup> A value of (default) means that the default user permissions for the service have not been changed

### Registry Settings

To start the Registry Editor, click **Start**, click **Run**, and in the **Run** dialog box, type `regedit` and press ENTER.

- `HKLM\SYSTEM\CurrentControlSet\Services\DHCP`
  - **User**: Network Service
  - **Permissions**: Full Control
  - **Details**: Required by DHCP Client Service

- `HKLM\SYSTEM\CurrentControlSet\Services\TCPIP`
  - **User**: Network Service
  - **Permissions**: Full Control
  - **Details**: Required by DHCP Client Service

## Security Considerations for Computers Running SQL Server

The following information suggests the security-related settings on computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].

### User Rights Assignment

To start the User Rights Assignment MMC Snap-in, click **Start**, click **Administrative Tools**, and then click **Local Security Policy**. In the **Local Security Policy** MMC snap-in, expand **Security Settings**, expand **Local Policies**, and then click **User Rights Assignment**.

|  Policy setting  |  Values | Reference and details |
|---|---|---|
|              Act as part of the operating system               |                  SQL Server Agent Service Account, SQL Server Service Account                   |         Required to run [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information see [Setting Up Windows Service Accounts](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions). |
|               Adjust memory quotas for a process               |                   SQL Server Agent Service Account,SQL Server Service Account                   |         Required to run [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information see [Setting Up Windows Service Accounts](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions).          |
|                    Bypass traverse checking                    |                   SQL Server Agent Service Account,SQL Server Service Account                   |         Required to run [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information see [Setting Up Windows Service Accounts](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions).  |
|                     Create global objects                      |                                   SQL Server Service Account                                    |                                          Required by SSIS service. For more information see [Setting Up Windows Service Accounts](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions).                                           |
| Enable computer and user accounts to be trusted for delegation | SQL Server Service Account, SQL Server Servers, BizTalk Server Servers, SQL Server Cluster Name | Required by BizTalk Server. Server name is in the form \<servername\>$. For more information, see [How to: Enable Kerberos Authentication on a SQL Server Failover Cluster](/previous-versions/sql/sql-server-2008-r2/ms189585(v=sql.105)). |
|                      Log on as a service                       |                   SQL Server Agent Service Account,SQL Server Service Account                   |         Required to run [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information see [Setting Up Windows Service Accounts](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions).          |
|                      Log on as a service                       |                                       SSO Service Account                                       |       Required to run Enterprise Single Sign-On Service. For more information about different user accounts, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).       |
|                      Log on as batch job                       |                   SQL Server Agent Service Account,SQL Server Service Account                   |         Required to run [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information see [Setting Up Windows Service Accounts](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions).          |
|                 Replace a process level token                  |                   SQL Server Agent Service Account,SQL Server Service Account                   |         Required to run [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information see [Setting Up Windows Service Accounts](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions).          |

### System Services

To start the Services MMC Snap-in, click **Start**, click **Run**, and in the **Run** dialog box, type `services.msc` and press ENTER.

- **DHCP Client**:
  - **Startup type** <sup>1</sup>: Automatic
  - **Details**: Required even if IP addresses are static
  - **User** <sup>2</sup>: (default)

- **Distributed Transaction Coordinator**:
  - **Startup type** <sup>1</sup>: Manual
  - **Details**: Service startup managed by Cluster Service

  The following user accounts need permissions to this service:

  ---
  | User <sup>2</sup>| Permissions | Details |
  | --- |  --- |  --- | 
  | SSO Service Account | Full Control | Required to start SSO service |
  | Network Service | Full Control | Required by IIS |

  ---

- **HTTP SSL** <sup>3</sup>:
  - **Startup type** <sup>1</sup>: Automatic
  - **Details**: Required by IIS
  - **User** <sup>2</sup>: (default)

- **IPSEC Services** <sup>3</sup>:
  - **Startup type** <sup>1</sup>: Automatic
  - **Details**: IPSEC increases network security if used
  - **User** <sup>2</sup>: (default)

- **Netlogon**:
  - **Startup type** <sup>1</sup>: (default)
  - **User** <sup>2</sup>: Local Service
  - **Permissions**: Full Control

- **NT LM Security Support Provider** <sup>3</sup>:
  - **Startup type** <sup>1</sup>: Automatic
  - **Details**: Required for Kerberos Authentication for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in SQL
  - **User** <sup>2</sup>: (default)

- **Remote Access Connection Manager**:
  - **Startup type** <sup>1</sup>: (default)

  The following user accounts need permissions to this service:

  ---
  | User <sup>2</sup>| Permissions | Details |
  | --- |  --- |  --- | 
  | SSO Service Account | Full Control | Required to start SSO service |
  | Network Service | Full Control | Required by IIS |

  ---

- **Server**:
  - **Startup type** <sup>1</sup>: Automatic
  - **Details**: Used for Clustered File Share resources
  - **User** <sup>2</sup>: Network Service
  - **Permissions**: Full Control

- **WinHTTP Web Proxy Auto-Discovery Service**:
  - **Startup type** <sup>1</sup>: (default)
  - **User** <sup>2</sup>: SSO Service Account
  - **Permissions**: Full Control
  - **Details**: Required to start SSO service

- **World Wide Web Publishing Service**:
  - **Startup type** <sup>1</sup>: Automatic
  - **Details**: Required by SQL Server Reporting Services
  - **User** <sup>2</sup>: (default)

 <sup>1</sup> A value of (default) means that the default settings applied by the security policy are not changed

 <sup>2</sup> A value of (default) means that the default user permissions for the service have not been changed

### Registry Settings
 To start the Registry Editor, click **Start**, click **Run**, and in the **Run** dialog box, type `regedit` and press ENTER.

- `HKLM\SYSTEM\CurrentControlSet\Services\DHCP`
  - **User**: Network Service
  - **Permissions**: Full Control
  - **Details**: Required by DHCP Client Service

- `HKLM\SYSTEM\CurrentControlSet\Services\TCPIP`
  - **User**: Network Service
  - **Permissions**: Full Control
  - **Details**: Required by DHCP Client Service

## Additional Security Considerations

The following table suggests the other important security-related settings for your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.


|  Affected artifact  |  Change |   Reference and details  |
|---|---|---|
| SSO Service Account | Grant Full Control Permission on Cluster in Cluster Manager |  This change is required for SSO to work properly   |
| SQL Server Service Account, SQL Server Servers, BizTalk Server Servers, SQL Server Cluster Name |  Trust for Delegation in Active Directory                 | Required for proper Kerberos authentication. For more information, see [How to: Enable Kerberos Authentication on a SQL Server Failover Cluster](/previous-versions/sql/sql-server-2008-r2/ms189585(v=sql.105)). |
| SQL Server Service Account  |  Grant permission to create SPN Entries |  Required for proper Kerberos authentication. For more information, see [How to use Kerberos authentication in SQL Server](/sql/database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections).             |
| SQL Server nodes, SQL cluster name |  Create SPN entries for user SQL Server Service Account  | Required for proper Kerberos authentication. For more information, see [How to use Kerberos authentication in SQL Server](/sql/database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections).  |
| SQL Network Name  cluster resource  | DNS Registration must succeed, Enable  Kerberos Authentication  |   Required for proper Kerberos authentication   |
| SQL Server Surface configuration  |  Enable Remote Direct Administrator Connection  |  Required by SQL Browser Service to function properly which is required by SQL Clients (BizTalk/ASP.NET) to correctly locate SQL Server named instance.  |
| BizTalk Application Users Group  | Grant Execute permission on **sp_help_jobhistory** in **msdb** database |   Required by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  |

## See Also

[Checklists for Other Important Tasks](~/technical-guides/checklists-for-other-important-tasks.md)
