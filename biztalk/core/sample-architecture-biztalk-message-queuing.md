---
description: "Learn more about: Sample Architecture: BizTalk Message Queuing"
title: "Sample Architecture: BizTalk Message Queuing"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Sample Architecture: BizTalk Message Queuing
This topic describes the sample architecture when you use the BizTalk Message Queuing adapter to send and receive messages.  
  
 The following figure shows the components of the BizTalk Server sample architecture when you use the BizTalk Message Queuing adapter.  
  
 **Figure 1 Sample architecture that shows BizTalk Message Queuing adapter**  
  
 ![Sample architecture for BizTalk Message Queuing](../core/media/tdi-sec-refarch-msmq.gif "TDI_Sec_RefArch_MSMQ")  
  
 This sample architecture contains the components as discussed in the following sections.  
  
## Perimeter network―Internet  
 We do not recommend using the Message Queuing binary protocol over the Internet. You should not let any Message Queuing traffic through Firewall 1. If you want to use the BizTalk Message Queuing adapter to receive messages over the Internet, do the following:  
  
-   Use a Message Queuing server in the perimeter network.  
  
-   Use the Message Queuing HTTP protocol over the Internet.  
  
-   Have a forwarding application in the perimeter network that picks up the messages from the Message Queuing server and forwards them to the BizTalk Message Queuing adapter by using a binary protocol.  
  
    > [!IMPORTANT]
    >  Even if you use BizTalk Message Queuing to receive messages from the Internet, the ports that BizTalk Message Queuing uses should remain closed in Firewall 1.  
  
## Perimeter network―intranet  
 When you use the BizTalk Message Queuing adapter to receive messages from the intranet, there is a Windows Message Queuing server that forwards the Message Queuing traffic to the BizTalk Server that runs a host instance of the BizTalk Message Queuing adapter.  
  
 If the intranet and the E-Business domain share a common Active Directory, a message goes through a series of Message Queuing routers until it reaches the right destination (the BizTalk Server that runs a host instance of the BizTalk Message Queuing receive adapter). This option is not represented in the diagram because it is less secure than the first one.  
  
## E-Business domain  
 The servers in this domain are:  
  
-   **BizTalk Server (processing, BizTalk Message Queuing adapter, and Tracking hosts).** This server has an installation of the BizTalk Server runtime, and has instances of the hosts that contain the BizTalk orchestrations, pipelines, Business Rule Engine, and other business processes. This is where the BizTalk Server ports, receive locations, pipelines, maps, schemas, and assemblies are located to receive, route, process, and send messages. This server also has a host instance of a host that supports tracking of health monitoring and business monitoring data. Additionally, this host contains instances of the host that runs the BizTalk Message Queuing send and receive adapters.  
  
    > [!NOTE]
    >  As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts.  
  
-   **Master secret server.** Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).  
  
-   **SQL Server.** Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).  
  
-   **Domain controller.** Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).  
  
-   **Administration tools.** Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).  
  
## See Also  
 [Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md)   
 [Sample Scenarios for Threat Model Analysis](../core/sample-scenarios-for-threat-model-analysis.md)
