---
title: "Checklist: Configuring Internet Information Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 186f82c0-bd50-4c79-a403-8b0d91cc68d6
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Configuring Internet Information Services
This topic lists steps that should be followed when preparing Internet Information Services (IIS) for use in a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.  
  
|Steps|Reference|  
|-----------|---------------|  
|Set up IIS to publish [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services and WCF services|-   See ["Enabling Web Services"](http://go.microsoft.com/fwlink/?LinkId=153335) (http://go.microsoft.com/fwlink/?LinkId=153335) in the BizTalk Server documentation.<br />-   See ["Configuring IIS for the Isolated WCF Receive Adapters"](http://go.microsoft.com/fwlink/?LinkId=202825)(http://go.microsoft.com/fwlink/?LinkId=202825) in the BizTalk Server documentation.|  
|Verify that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services and WCF services are working correctly.|-   See ["Testing Published Web Services"](http://go.microsoft.com/fwlink/?LinkId=153336) (http://go.microsoft.com/fwlink/?LinkId=153336) in the BizTalk Server documentation.<br />-   See ["How to Create a .NET Application to Test a WCF Service Published with the BizTalk WCF Service Publishing Wizard"](http://go.microsoft.com/fwlink/?LinkId=202830) (http://go.microsoft.com/fwlink/?LinkId=202830) in the BizTalk Server documentation.|  
|Lock down [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services:<br /><br /> -   Turn off the Debug switch in the web.config or machine.config file.<br />-   Configure so that POST is the only verb allowed.|-   See Microsoft Knowledge Base Article 815145, ["HOW TO: Lock Down an ASP.NET Web Application or Web Service"](http://go.microsoft.com/fwlink/?LinkId=153337) (http://go.microsoft.com/fwlink/?LinkId=153337).<br />-   See ["ASP.NET Edit Rule Dialog Box"](http://go.microsoft.com/fwlink/?LinkID=64566) (http://go.microsoft.com/fwlink/?LinkID=64566) in the .NET Framework 2.0 documentation.|  
|Configure load balancing by using NLB (or other load balancer) to balance load across BizTalk Server Web services and WCF services.|-   **For Windows Server 2008**: See ["Network Load Balancing Deployment Guide"](http://go.microsoft.com/fwlink/?LinkId=153139) (http://go.microsoft.com/fwlink/?LinkId=153139).<br />-   **For Windows Server 2003**: See ["Network Load Balancing: Configuration Best Practices for Windows 2000 and Windows Server 2003"](http://go.microsoft.com/fwlink/?LinkID=69529) (http://go.microsoft.com/fwlink/?LinkID=69529).|  
|Change IIS and ASP.NET settings for tuning Web services. **Note:**  ASP.NET 2.0 includes auto-tuning, so modifying these settings should not be needed for the web.config file of ASP.NET 2.0 Web sites where autoConfig is enabled in the \<processModel\> section. “autoConfig=true” is the default setting.|Review the "ASP.NET settings that can impact HTTP or SOAP Adapter performance” section of the topic ["Configuration Parameters that Affect Adapter Performance"](http://go.microsoft.com/fwlink/?LinkId=153338) (http://go.microsoft.com/fwlink/?LinkId=153338) in the BizTalk Server documentation.|  
|Implement an approach for publishing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services and WCF services.|-   See [Publishing Internet-facing Web Services and WCF Services](../technical-guides/publishing-internet-facing-web-services-and-wcf-services.md).<br />-   See ["Publishing WCF Services"](http://go.microsoft.com/fwlink/?LinkId=202827) (http://go.microsoft.com/fwlink/?LinkId=202827) in the BizTalk Server documentation.|  
|Follow best practices for optimizing IIS performance.|See ["Top Ten Ways To Pump Up IIS Performance"](http://go.microsoft.com/fwlink/?LinkId=109107) (http://go.microsoft.com/fwlink/?LinkId=109107).|  
|Follow best practices for writing high performance web applications for IIS.|See ["10 Tips for Writing High-Performance Web Applications"](http://go.microsoft.com/fwlink/?LinkId=98290) (http://go.microsoft.com/fwlink/?LinkId=98290).|  
  
## In This Section  
  
-   [Publishing Internet-facing Web Services and WCF Services](../technical-guides/publishing-internet-facing-web-services-and-wcf-services.md)