---
description: "Learn more about: Managing BizTalk Server Security"
title: "Managing BizTalk Server Security"
ms.custom: "biztalk-2020"
ms.date: "01/13/2020"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---

# Managing BizTalk Server Security

Maintaining a secure Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment requires that you manage accounts, certificates, and passwords.

## BizTalk Server groups

To help ensure the security of the business documents handled by BizTalk Server, BizTalk Server administrators manage the following accounts and certificates:  
  
- **BizTalk Server Administrators group**: For users to perform administrative tasks either through the BizTalk Administration console or by using the Microsoft Windows Management Instrumentation (WMI) provider, they must be granted the proper privileges in Microsoft SQL Server and Microsoft Windows. For more information about the privileges for administrative tasks, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
   For information about adding users to the BizTalk Server Administrators group or removing users from the BizTalk Server Administrators group, see [How to Manage the BizTalk Server Administrators Group](../core/how-to-manage-the-biztalk-server-administrators-group.md).  
  
   For more information about Enterprise Single Sign-On, see [Using SSO](../core/using-sso.md).  
  
- **BizTalk Server Operators group**: The BizTalk Server Operator is a low privileged role that only has access to monitoring and troubleshooting actions.  
  
   Members of the BizTalk Server Operators group can do the following:  
  
  - View service state and message flow.  
  
  - Start or stop applications.  
  
  - Start or stop orchestrations.  
  
  - Start or stop send ports or send port groups.  
  
  - Enable or disable receive locations. The changes do not take effect until the next cache refresh interval of 60 seconds, which is the default. The cache refresh interval is set at the BizTalk Server group level.  
  
  - Terminate and resume service instances.  
  
    Members of the BizTalk Server Operators group cannot do the following:  
  
  - Modify the configuration for BizTalk Server.  
  
  - View message context properties classified as Personally Identifiable Information (PII) or message bodies.  
  
  - Modify the course of message routing, such as removing or adding new subscriptions to the running system, including the ability to publish messages into the BizTalk Server runtime.  
  
  > [!NOTE]
  > - If a user who is a member of the BizTalk Server Operators group is also a local administrator on the computers running BizTalk Server, this user can access data beyond the role of the Operators group on these computers. For more information, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  >
  > - If you want to allow a user who is a member of the BizTalk Server Operators group to monitor remote BizTalk servers, this user must also be a member of the local Administrators group on the remote computers.  
  
- **BizTalk Server Read Only Users group**: This is a new group **starting with BizTalk Server 2020**. Members in this group can view Artifacts, service state, message flow, and tracking information. Members do not have privileges to perform any administrative operations.  
  
  Members of the BizTalk Server Read Only Users group can do the following:
  
  - View user artifact information
  
  - View platform artifact such as Receive Port, Receive Location, Send Port, Orchestration, Maps, Policies, Pipelines, Host, Host Instances and Adapters 

  - View Message Flow and Message events. Cannot view Message Context and Message content.

  - View general service instances details and error information.

  - View tracking information.

  - View Parties and Agreement information.

  - View Group Hub Page, execute query, save query and load query.

  - Can export Binding, Policies, and MSI but cannot import.
  
  > [!NOTE]
  >  If a user who is a member of the BizTalk Server Read Only Users group is also a local administrator on the computers running BizTalk Server, this user can access data beyond the role of the Operators group on these computers. For more information, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
- **Hosts and service accounts**: When creating a host and its associated host instances, you must provide the Windows group for the host and the service account credentials for each host instance. You must ensure that the host instance service accounts are members of the Windows group for the host.  
  
- **Signing certificates**: Signing certificates (private key certificates) are specified for the BizTalk group. These are optional and can be changed at any time by a BizTalk Server administrator.  
  
  For more complete information about Windows accounts that BizTalk Server uses, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
## Next steps
  
-   [Best Practices for Managing Windows Groups and User Accounts](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)  
  
-   [Best Practices for Managing Certificates](../core/best-practices-for-managing-certificates1.md)  
  
-   [Managing Windows Groups and User Accounts](../core/managing-windows-groups-and-user-accounts.md)
