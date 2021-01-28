---
description: "Learn more about: Sample Architectures for Small &amp; Medium-Sized Companies"
title: "Sample Architectures for Small &amp; Medium-Sized Companies | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "architecture, examples"
ms.assetid: fc8c2fdd-bcb1-481c-b351-03092dd48540
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sample Architectures for Small &amp; Medium-Sized Companies
This section provides a sample architecture to deploy Microsoft BizTalk Server when you want to help to protect the assets in a small or medium-sized company. While these architectures encourage defense in depth and separation of services to minimize the impact of an attack, they assume quantities of hardware, software, and human resources that are generally available to large companies.

 However, small and medium-sized companies (or large companies with small BizTalk Server deployments) should also be concerned with how to protect their environments. After we looked at how companies deployed or plan to deploy their [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solutions, we derived a sample architecture for small and medium-sized companies that balances available resources with the greatest possible security. You should use the information in this section to help you plan your own deployment. After you evaluate your business needs and assets you might decide on a different architecture for your BizTalk Server deployment.

 To make it easier to see how your architecture would look, this section provides sample architectures based on various adapters that you might use in your environment. The figures show you which components of the topology are adapter-independent, and which components depend on the adapter you use in your BizTalk Server environment.

 We also examine usage scenarios based on some of the adapters you can use with BizTalk Server. To help you as you plan and design your own architecture, we provide a threat model analysis of this sample architecture. This analysis gives you a deeper look at the potential security issues that might affect your company, depending on the adapters you use to communicate with your partners.

 While this section gives you information to help you design a secure deployment of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], to increase the security in your environment you should also consider securing the communication between the servers in the environment.

> [!IMPORTANT]
>  This section assumes that you are not using Business Activity Monitoring (BAM). This feature requires additional security considerations. This is discussed in [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).

> [!NOTE]
>  For more information about adapters not described in this document, see the BizTalk Server Developer Center ([https://go.microsoft.com/fwlink/?LinkId=46420](https://go.microsoft.com/fwlink/?LinkId=46420).)

## In This Section

-   [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md)

-   [Sample Architecture: HTTP and SOAP Adapters](../core/sample-architecture-http-and-soap-adapters.md)

-   [Sample Architecture: BizTalk Message Queuing](../core/sample-architecture-biztalk-message-queuing.md)

-   [Sample Architecture: FTP Adapter](../core/sample-architecture-ftp-adapter.md)

-   [Sample Architecture: File Adapter](../core/sample-architecture-file-adapter.md)
