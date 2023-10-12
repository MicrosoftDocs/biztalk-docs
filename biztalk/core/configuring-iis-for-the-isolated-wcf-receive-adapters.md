---
description: "Learn more about: Configuring IIS for the Isolated WCF Receive Adapters"
title: "Configuring IIS for the Isolated WCF Receive Adapters"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring IIS for the Isolated WCF Receive Adapters
To publish WCF services by using the BizTalk WCF Service Publishing Wizard, you must configure Internet Information Services (IIS), BizTalk isolated hosts, and Windows user group accounts. This section discusses issues related to configuring IIS for publishing WCF services with isolated WCF receive adapters such as the WCF-BasicHttp receive adapter, WCF-WSHttp receive adapter, and WCF-CustomIsolated adapter. For general information about hosting WCF services in IIS, see "Hosting in IIS" at [https://go.microsoft.com/fwlink/?LinkId=75700](/dotnet/framework/wcf/feature-details/hosting-in-internet-information-services).

## Considerations When Configuring IIS
 **Internet Information Services 7.0 and 7.5**

 You can use IIS 7.0 and 7.5 configured with ASP.NET 4.0 to publish WCF services with isolated WCF receive adapters.

 IIS 7.0 (for Windows Server 2008 SP2) and IIS 7.5 (for Windows Server 2008 R2) use the IIS application pools for processing Web service requests. IIS 7.0 supports multiple application pools. Each application pool process can run under a different user context.

 **BizTalk isolated hosts**

 To host the WCF services with isolated WCF receive adapters, you must create at least one isolated host in BizTalk Server. For more information about how to configure BizTalk isolated hosts, see "BizTalk Isolated Hosts" in [Enabling Web Services](../core/enabling-web-services.md).

 **Database access for multiple server installations**

 If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the BizTalk Management database reside on different servers, you should change the user context of the IIS Application Pool to a domain user account.

 When implementing a multi-server deployment, the Isolated Host Windows groups must exist on the domain to which the BizTalk database servers belong.

 **Minimizing account privileges and user rights**

 You use isolated hosts to give adapters that run in external processes access to the minimal amount of required resources to interact with BizTalk Server. For a secure deployment, you should give the user context for the external processes minimal privileges.

 **Security recommendations for the BizTalk Web Services Publishing Wizard**

 The virtual directory created by the BizTalk WCF Service Publishing Wizard inherits the access control lists (ACL) from the parent virtual directory or Web site.

## See Also
 [Publishing WCF Services](../core/publishing-wcf-services.md)