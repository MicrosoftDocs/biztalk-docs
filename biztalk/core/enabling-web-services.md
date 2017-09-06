---
title: "Enabling Web Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Web services, publishing"
  - "hosts, isolated"
  - "Web services, planning"
  - "Web services, enabling"
ms.assetid: 2a4681f6-9ded-423d-baa5-5831e6a85c61
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Enabling Web Services
To publish Web services, you must configure Internet Information Services (IIS), BizTalk Isolated Hosts, and Windows user and group accounts. This section discusses how to enable Web services in IIS. For more information about enabling Web services, see the IIS documentation.  
  
 **Internet Information Services**  
  
 You can publish Web services to Windows systems that have IIS configured with ASP.NET. For each server, all Web services run within the ASP.NET worker process.  
  
 The ASP.NET worker process uses the local ASPNET account by default. IIS uses application pools for processing Web service requests.  
  
 **BizTalk Isolated Hosts**  
  
 To enable Web services, you must create at least one Isolated Host in BizTalk Server. Isolated Hosts represent external processes, such as ISAPI extensions and ASP.NET processes that BizTalk Server does not create or control. These types of external processes must host certain adapters, such as HTTP/S and SOAP.  
  
 The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Manager creates the BizTalkServerIsolatedHost that BizTalk uses as the default Isolated Host. The BizTalk Isolated Host Users group is the name of the Windows group associated with this host by default. For more information about Hosts and Host Instances, see [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md).  
  
 An isolated host instance can run only one adapter. If you configure the receive handlers of HTTP and SOAP adapters with the one isolated host, you must create two application pools, one application pool for each adapter.  
  
 For example, if you plan to configure two isolated hosts as following:  
  
|Isolated host name|Receive locations|  
|------------------------|-----------------------|  
|Isolated Host 1|HTTP_ReceiveLocation1A<br /><br /> HTTP_ReceiveLocation1B<br /><br /> SOAP_ReceiveLocation1 **Note:**  The **Isolated Host 1** is used for receive handlers of both SOAP and HTTP adapters.|  
|Isolated Host 2|HTTP_ReceiveLocation2|  
  
 You may create four virtual directories, one for each receive location as follows:  
  
|Receive location|Virtual directory|  
|----------------------|-----------------------|  
|HTTP_ReceiveLocation1A|IIS_Virtual_Directory1A|  
|HTTP_ReceiveLocation1B|IIS_Virtual_Directory1B|  
|SOAP_ReceiveLocation1|IIS_Virtual_Directory1C|  
|HTTP_ReceiveLocation2|IIS_Virtual_Directory2|  
  
 Then, you must create at least three application pools for the virtual directories as follows:  
  
> [!NOTE]
>  You must create at least one application pool for each isolated host.  
  
|Virtual directories|Application pool|Description|  
|-------------------------|----------------------|-----------------|  
|IIS_Virtual_Directory1A<br /><br /> IIS_Virtual_Directory1B|AppPool_Host1_HTTP|A separate application pool is not required because all of the receive locations have the same isolated host (Isolated Host 1), and the same protocol.|  
|IIS_Virtual_Directory1C|AppPool_Host1_SOAP|A separate application pool is required because the receive location uses the different protocol (SOAP) from the other receive locations in the same host (Isolated Host 1).|  
|IIS_Virtual_Directory2|AppPool_Host2_HTTP|A separate application pool is required because the receive location runs under the different host from Isolated Host 1.|  
  
> [!NOTE]
>  You must add the user account for the application pools to the appropriate local or domain groups of the isolated hosts. For more information, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
> [!NOTE]
>  You need to match the user account between an isolated host instance and the corresponding application pool according to the previous tables. For more information about the relationship between user accounts of isolated host instance and application pools, see [How to Change Service Accounts and Passwords](../core/how-to-change-service-accounts-and-passwords.md).  
  
 **Database access for single server installations**  
  
 If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the BizTalk Management database reside on the same server, you should set the user context of the ASP.NET worker process or the IIS Application Pool to the local ASPNET user account, or a local or domain user account that has minimal privileges.  
  
 **Database access for multiple server installations**  
  
 If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the BizTalk Management database reside on different servers, you should change the user context of the ASP.NET worker process or the IIS Application Pool to a domain user account.  
  
 When implementing a multi-server deployment, the Isolated Host Windows groups must exist on the domain which the BizTalk database servers belong to.  
  
 **Minimizing account privileges and user rights**  
  
 You use Isolated Hosts to give adapters that run in external processes access to the minimal amount of required resources to interact with BizTalk Server. For a secure deployment, you should give the user context for the external processes minimal privileges.  
  
 **Security recommendations for BizTalk Web Services Publishing Wizard**  
  
 The virtual directory created by the BizTalk Web Services Publishing Wizard will inherit the access control lists (ACL) and authentication requirements from the parent virtual directory or Web site. If the parent virtual directory or Web site allows anonymous access, the BizTalk Web Services Publishing Wizard will remove that capability when creating the virtual directory.  
  
 The following contains security notes and recommendations for [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)].  
  
## Next
  
[How to Enable ASP.NET for Published Web Services](../core/how-to-enable-asp-net-4-0-for-published-web-services.md)