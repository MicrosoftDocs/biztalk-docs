---
description: "Learn more about: Publishing Internet-facing Web Services and WCF Services"
title: "Publishing Internet-facing Web Services and WCF Services"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Publishing Internet-facing Web Services and WCF Services
You can use multiple approaches for publishing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services and WCF services to the Internet:

- Use reverse proxy rules in a perimeter network (also known as DMZ, demilitarized zone, and screened subnet).

- Put the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that publish the Web services or WCF services into the perimeter network domain.

- Use BizTalk Server cloud enabler functionality to publish the Web services or WCF services as an Azure AppFabric Service Bus relay endpoint.

## Using a Reverse Proxy
 This has been the traditional approach for publishing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services and WCF services. Using reverse proxy rules in the perimeter network obviates the need to have BizTalk servers located in the perimeter network. The reverse proxy rules simply forward the HTTP and SOAP requests from the perimeter network to the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the intranet domain.

 For more information about using a reverse proxy, see the following topics in BizTalk Server Help:

-   ["Sample Architecture: HTTP and SOAP Adapters"](../core/sample-architecture-http-and-soap-adapters.md) (https://go.microsoft.com/fwlink/?LinkId=153339).

-   ["Sample TMA: HTTP and SOAP Adapters"](../core/sample-tma-http-and-soap-adapters.md) (https://go.microsoft.com/fwlink/?LinkId=153340).

-   ["Large Distributed Architecture"](../core/large-distributed-architecture.md) (https://go.microsoft.com/fwlink/?LinkId=153341).

## Using Computers Running BizTalk Server in the Perimeter Network
 This is not the preferred approach for publishing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services or WCF services to the Internet because it requires computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to be located in the perimeter network. However, when a reverse proxy is not available in the perimeter network, you can use this approach.

 This approach requires the perimeter network domain to enlist in a one-way trust with the intranet domain (but the intranet domain does not trust the perimeter network domain). The IIS application pools that host the Web services or WCF services in the perimeter network domain must be running under an intranet domain account that is in the "BizTalk Isolated Host Users" domain group. This gives the application pool the required rights to publish messages to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database.

 You must open specific ports in the firewall to accommodate this. For more information about the required ports, see ["Ports for the Receive and Send Servers"](../core/ports-for-the-receive-and-send-servers.md) (<https://go.microsoft.com/fwlink/?LinkId=153342>) in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.

## Exposing BizTalk Applications on the Cloud using AppFabric Connect for Services
 See the article [Exposing BizTalk Applications on the Cloud using AppFabric Connect for Services](/archive/technet-wiki/1664.expose-biztalk-applications-on-the-cloud-using-appfabric-connect-for-services) (/archive/technet-wiki/1664.expose-biztalk-applications-on-the-cloud-using-appfabric-connect-for-services) for more information about expose BizTalk Applications as WCF Services on the cloud.

## See Also
 [Planning for Publishing Web Services1](../technical-guides/planning-for-publishing-web-services1.md)
