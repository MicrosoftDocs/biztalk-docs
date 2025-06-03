---
description: "View a list of questions designed to help you plan how to publish Web services in BizTalk Server."
title: "Publish web Services planning"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Planning for Publishing Web Services

[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides built-in support for Web services. It enables you to reuse and aggregate your existing Web services within your orchestrations.  

## Overview

 You can also publish (expose) your orchestrations as Web services to separate the Web service logic from the business process logic, which allows you to update or replace the business logic as needed without touching the code used for the Web service logic. This functionality is referred to as implementing "modular code." In general it is considered a best practice to implement modular code where possible. Publishing Web services requires that you enable Web services and that you publish an orchestration or schema as a Web service using the BizTalk Web Services Publishing Wizard.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] implements support for native adapters in Web services through the use of the SOAP adapter. Native adapter support provides scalability, fault tolerance, and tracking capabilities for Web services without writing a single line of code. For more information about the SOAP adapter, see [SOAP Adapter](../core/soap-adapter.md).  
  
Planning for Web services can be divided into two categories, planning for publishing Web services and planning for consuming Web services. This topic describes the steps that you should follow for publishing Web services.  
  
## Enabling Web Services  
 To publish Web services, you must configure Internet Information Services (IIS), BizTalk Isolated Hosts, and Windows user and group accounts. This section provides an overview about enabling web services. For more information about enabling Web services, see the IIS documentation.  
  
### Internet Information Services
 You can publish Web services to Windows systems that have IIS configured with ASP.NET. In IIS, all Web services run within the ASP.NET worker process.  
  
 IIS uses application pools for processing Web service requests. IIS supports multiple application pools and each application pool process can run under a different user context.  
  
### BizTalk Isolated Hosts  
 To enable Web services, you must create at least one isolated host in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Isolated hosts represent external processes, such as ISAPI extensions and ASP.NET processes that BizTalk Server does not create or control. These types of external processes must host certain adapters, such as HTTP/S and SOAP.  
  
 The BizTalk Server Configuration Manager creates the BizTalkServerIsolatedHost that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses as the default isolated host. The BizTalk Isolated Host Users group is the name of the Windows group associated with this host by default. For more information about hosts and host instances, see [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md).  
  
 An isolated host instance can run only one adapter. If you configure the receive handlers of HTTP and SOAP adapters with the one isolated host, you must create two application pools, one application pool for each adapter.  
  
 For example, if you plan to configure two isolated hosts, as follows:  
  
|Isolated Host Name|Receive Locations|  
|------------------------|-----------------------|  
|Isolated Host 1|HTTP_ReceiveLocation1A<br /><br /> HTTP_ReceiveLocation1B<br /><br /> SOAP_ReceiveLocation1 **Note:**  The **Isolated Host 1** is used for receive handlers of both SOAP and HTTP adapters.|  
|Isolated Host 2|HTTP_ReceiveLocation2|  
  
 You may create four virtual directories, one for each receive location, as follows:  
  
|Receive Location|Virtual Directory|  
|----------------------|-----------------------|  
|HTTP_ReceiveLocation1A|IIS_Virtual_Directory1A|  
|HTTP_ReceiveLocation1B|IIS_Virtual_Directory1B|  
|SOAP_ReceiveLocation1|IIS_Virtual_Directory1C|  
|HTTP_ReceiveLocation2|IIS_Virtual_Directory2|  
  
 Then you must create at least three application pools for the virtual directories as follows:  
  
> [!NOTE]  
>  You must create at least one application pool for each isolated host.  
  
|Virtual Directories|Application Pool|Description|  
|-------------------------|----------------------|-----------------|  
|IIS_Virtual_Directory1A<br /><br /> IIS_Virtual_Directory1B|AppPool_Host1_HTTP|A separate application pool is not required because all of the receive locations have the same isolated host (Isolated Host 1), and the same protocol.|  
|IIS_Virtual_Directory1C|AppPool_Host1_SOAP|A separate application pool is required because the receive location uses the different protocol (SOAP) from the other receive locations in the same host (Isolated Host 1).|  
|IIS_Virtual_Directory2|AppPool_Host2_HTTP|A separate application pool is required because the receive location runs under the different host from Isolated Host 1.|  
  
 Keep the following important points in mind as you create your application pools:  
  
-   You must add the user account for the application pools to the appropriate local or domain groups of the isolated hosts. See [Windows Group and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
-   You need to match the user account between an isolated host instance and the corresponding application pool according to the previous tables. For more information about the relationship between user accounts of isolated host instance and application pools, see [How to Change Service Accounts and Passwords](../core/how-to-change-service-accounts-and-passwords.md).  
  
### Database Access for Single Server Installations  
 If BizTalk Server and the BizTalk Management database reside on the same server, you should set the user context of the ASP.NET worker process or the IIS Application Pool to the local ASPNET user account, or to a local or domain user account that has minimal privileges.  
  
### Database Access for Multiple Server Installations  
 If BizTalk Server and the BizTalk Management database reside on different servers, you should change the user context of the ASP.NET worker process or the IIS Application Pool to a domain user account.  
  
 When implementing a multi-server deployment, the Isolated Host Windows groups must exist on the domain that the BizTalk database servers belong to.  
  
### Minimizing Account Privileges and User Rights  
 You use isolated hosts to give adapters that run in external processes access to the minimal amount of required resources to interact with BizTalk Server. For a more secure deployment, you should give the user context for the external processes minimal privileges.  
  
### Security Recommendations for BizTalk Web Services Publishing Wizard  
 The virtual directory created by the BizTalk Web Services Publishing Wizard will inherit the access control lists (ACL) and authentication requirements from the parent virtual directory or Web site. If the parent virtual directory or Web site allows anonymous access, the BizTalk Web Services Publishing Wizard will remove that capability when creating the virtual directory.  
  
### Enabling ASP.NET 4.0 for Published Web Services  
See [How to Enable ASP.NET 4.0 for Published Web Services](../core/how-to-enable-asp-net-4-0-for-published-web-services.md).  
  
## Using the BizTalk Web Services Publishing Wizard  
 For more information about publishing an orchestration as a Web service, see [Publishing an Orchestration as a Web Service](../core/publishing-an-orchestration-as-a-web-service.md).  
  
 For more information about publishing schemas as a Web service, see [Publishing Schemas as a Web Service](../core/publishing-schemas-as-a-web-service.md).  
  
## Planning for Publishing WCF Services  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] introduces built-in support for Windows Communication Foundation (WCF). [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to reuse and aggregate all your existing WCF services within your orchestrations. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] also implements support for native adapters in WCF services. Native adapter support provides scalability, fault tolerance, and tracking capabilities for WCF services without requiring you to write code. For information about the WCF adapters, see [WCF Adapters](../core/wcf-adapters.md).  
  
 For more information about planning for WCF Services in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Publishing WCF Services](../core/publishing-wcf-services.md).  
  
## See Also  
 [Planning for Consuming Web Services](../technical-guides/planning-for-consuming-web-services.md)
