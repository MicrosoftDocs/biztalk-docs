---
description: "Learn more about: Checklist: Configuring Internet Information Services"
title: "Checklist: Configuring Internet Information Services"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Checklist: Configuring Internet Information Services

This topic lists steps that should be followed when preparing Internet Information Services (IIS) for use in a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.

- Set up IIS to publish [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services and WCF services. For more information, go to:

  - [Enabling Web Services](../core/enabling-web-services.md)
  - [Configuring IIS for the Isolated WCF Receive Adapters](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)

- Verify that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services and WCF services are working correctly. For more information, go to:

  - [Testing Published Web Services](../core/testing-published-web-services.md)
  - [How to Create a .NET Application to Test a WCF Service Published with the BizTalk WCF Service Publishing Wizard](../core/use-net-application-to-test-wcf-service-published-with-wcf-service-publishing.md)

- Lock down [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services:

  - Turn off the Debug switch in the web.config or machine.config file.
  - Configure so that POST is the only verb allowed.

  For more information, go to:

  - [Secure applications that are built on the .NET Framework](/troubleshoot/developer/dotnet/framework/general/secure-applications)
  - [ASP.NET Edit Rule Dialog Box](/previous-versions/dotnet/netframework-2.0/ms186183(v=vs.80))

- Configure load balancing by using NLB (or other load balancer) to balance load across BizTalk Server Web services and WCF services.

- Change IIS and ASP.NET settings for tuning Web services. ASP.NET 2.0 includes auto-tuning, so modifying these settings should not be needed for the web.config file of ASP.NET 2.0 Web sites where autoConfig is enabled in the `<processModel>` section. `autoConfig=true` is the default setting.

  Review the "ASP.NET settings that can impact HTTP or SOAP Adapter performance” section in [Configuration Parameters that Affect Adapter Performance](../core/configuration-parameters-that-affect-adapter-performance.md).

- Implement an approach for publishing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services and WCF services. For more information, go to:

  - [Publishing Internet-facing Web Services and WCF Services](publishing-internet-facing-web-services-and-wcf-services.md)
  - [Publishing WCF Services](../core/publishing-wcf-services.md)

- Follow best practices for optimizing IIS performance. For more information, go to [Tuning IIS 10.0](/windows-server/administration/performance-tuning/role/web-server/tuning-iis-10)

- Follow best practices for writing high performance web applications for IIS. For more information, go to [10 Tips for Writing High-Performance Web Applications](/archive/msdn-magazine/2005/january/asp-net-10-tips-for-writing-high-performance-web-applications).

## In This Section

- [Publishing Internet-facing Web Services and WCF Services](../technical-guides/publishing-internet-facing-web-services-and-wcf-services.md)
