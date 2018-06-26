---
title: "Planning for Sending and Receiving | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d67e5f7-5127-4c1d-be20-8d8dbb538286
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for Sending and Receiving
Nearly every document that is processed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is received by a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive adapter, and sent from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] using a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send adapter. Because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters figure so prominently in any [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, it is important to plan ahead to determine which adapters or accelerators you will be using and how to correctly configure these adapters and/or accelerators.  
  
## Determining Which Adapters and Accelerators You Will Use  
 Confer with your trading partners in advance to determine which adapters and accelerators you will need to facilitate sending and receiving documents between your organization and your trading partners, and between your BizTalk applications and your internal business applications. Design your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architecture to be flexible enough to accommodate adding additional adapters or accelerators in the event that you establish relationships with additional trading partners in the future.  
  
## Functionality Supported by BizTalk Adapters  
 The table in this section lists the primary benefit of each native adapter and whether the adapter provides the following features:  
  
-   **Transaction support** The ability to send and receive documents under the context of a distributed transaction coordinator (DTC) transaction. This functionality is required for maintaining ordered message delivery and to guarantee that documents are not duplicated or lost.  
  
    > [!NOTE]  
    >  If you encounter problems with MSDTC, review the topic [Troubleshooting Problems with MSDTC](http://go.microsoft.com/fwlink/?LinkID=154693) (http://go.microsoft.com/fwlink/?LinkID=154693).  
  
-   **Two-way communication support (Request/Response or Solicit/Response)** The ability to send a document and process a response message from the destination or to receive a document and send a response message to the source.  
  
-   **In-order receive support.** The ability to publish received documents to the MessageBox database in the exact order that the documents were received.  
  
    > [!NOTE]  
    >  Certain adapters can enforce ordered document delivery at the receive location level, while other adapters cannot. Ordered delivery can still be enforced at the send port level for those adapters which do not support ordered document delivery at the receive location level but doing so may incur a performance penalty. For more information about ordered delivery of messages, see the topic [Ordered Delivery of Messages](http://go.microsoft.com/fwlink/?LinkId=155751) (http://go.microsoft.com/fwlink/?LinkId=155751).  
  
-   **SSO enabled.** The ability to use SSO authentication when sending or receiving documents with the adapter.  
  
|Adapter|Primary Benefit|Transaction Support|Two-Way Communication Support|In-Order Receive Support|SSO Enabled|  
|-------------|---------------------|-------------------------|------------------------------------|-------------------------------|-----------------|  
|File|Easy to use|No|No|No|No|  
|FTP|Is widely used for business-to-business communications|No|No|No|Yes|  
|HTTP(s)|Is widely used for business-to-business communications|No|Request/Response and Solicit/Response|No|Yes|  
|SOAP|Supports the use of Web services|No|Request/Response and Solicit/Response|No|Yes|  
|MSMQ|Supports guaranteed once-only delivery of messages between BizTalk Server and Microsoft Message Queuing|Yes|No|Yes|No|  
|MQ Series|Supports guaranteed once-only delivery of messages between BizTalk Server and IBM WebSphere MQ for Windows platforms|Yes|No|Yes|Yes|  
|SQL|Supports direct communication between BizTalk Server and SQL Server databases|Yes|Solicit/Response only|No|No|  
|Windows SharePoint Services|Enables the exchange of XML and binary messages between BizTalk Server and SharePoint document libraries|No|No|No|No|  
|POP3|Supports receiving documents through e-mail|No|No|No|No|  
|SMTP|Supports sending documents through e-mail|No|No|No|No|  
|EDI|Supports processing of business documents that conform to the EDI standard|No|No|No|No|  
|Custom|Supports your legacy system|Yes, requires custom code.|Yes, requires custom code.|Yes, requires custom code.|Yes, requires custom code.|  
|WCF-WSHttp|Supports WS-* standards over the HTTP transport|Yes, transactions are supported on WsHTTP (only WS-Transactions)|Request/Response and Solicit/Response|No|Yes|  
|WCF-BasicHttp|Communicates with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1 using HTTP or HTTPS|No|Request/Response and Solicit/Response|No|Yes|  
|WCF-NetTcp|Supports WS-* standards over the TCP transport|Yes|Request/Response and Solicit/Response|No|Yes|  
|WCF-NetMsmq|Supports queuing by leveraging Microsoft Message Queuing (MSMQ) as a transport|Yes|No|Yes|Yes|  
|WCF-NetNamedPipe|Provides a fast transport for cross-process communication on the same computer (only for WCF apps)|Yes|Request/Response and Solicit/Response|No|Yes|  
|WCF-Custom|Enables the use of WCF extensibility features|Yes.|Yes.|Yes, as long as the binding supports it.|Yes.|  
|WCF-CustomIsolated|Enables the use of WCF extensibility features over the HTTP transport|Yes.|Yes.|No.|Yes.|  
  
## Line of Business Adapters  
 Following is a list of the Line of Business (LOB) adapters provided by Microsoft.  
  
> [!NOTE]  
>  With the exception of the Microsoft BizTalk Adapter v2.0 for mySAP™ Business Suite (the Adapter), none of the Line of Business adapters are supported on Windows Vista.  
  
|Adapter|Description|Supported Versions|  
|-------------|-----------------|------------------------|  
|SAP (also referred to as "the Adapter")|Enables exchange of Intermediate Document (IDOC), BAPI, and remote function call (RFC) messages between BizTalk Server and an SAP R/3® system.|SAP R/3 4.x and R/3 6.20 (Enterprise)|  
|PeopleSoft Enterprise|Enables exchange of Component Interface (CI) messages between BizTalk Server and a PeopleSoft system.|PeopleTools Versions 8.17.02, 8.43, 8.45, 8.46 and 8.48|  
|JD Edwards OneWorld XE|Enables exchange of Business Function messages between BizTalk Server and a JD Edwards OneWorld system.|B7.3.3.3 with SP23 and JDE 8.0 (B7.3.3.4)|  
|JD Edwards EnterpriseOne|Enables exchange of Business Function messages between BizTalk Server and a JD Edwards EnterpriseOne system.|8.10 & 8.11 with Tools Release 8.93, 8.94, 8.95 and 8.96|  
|ODBC Adapter for Oracle Database|Enables reading and writing information from and to an Oracle Server database.|Oracle 8i (8.1.6.0), 9i (9.2.0.1), or 10g|  
|Siebel eBusiness Applications|Enables exchange of Business Components and Business Service messages between BizTalk Server and a Siebel eBusiness Application.|7.0, 7.5.*, 7.7.\*, and 7.8.\*|  
|TIBCO Rendezvous|Enables exchange of XML and binary data format messages between BizTalk Server and TIBCO Rendezvous.|7.3|  
|TIBCO Enterprise Message Service|Enables exchange of XML and binary data format messages between BizTalk Server and a TIBCO EMS server providing a tightly integrated and reliable application infrastructure.|4.2|  
|WebSphere MQ|Enables exchange of messages between BizTalk Server and IBM WebSphere MQ.|5.3 with Fix Pack 10 or later and 6.0 with Fix Pack 1.1 or later|  
  
 For more information about the LOB adapters available with BizTalk Server, see [Adapters included with BizTalk Server 2010](http://go.microsoft.com/fwlink/?LinkId=152664) (http://go.microsoft.com/fwlink/?LinkId=152664).  
  
## BizTalk Adapter Pack  
 Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] contains WCF-based adapters to provide connectivity to LOB applications such as Oracle Database, Oracle E-Business Suite, SAP, Siebel, and SQL Server. For a list of adapters available with [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], see [BizTalk Adapter Pack](http://go.microsoft.com/fwlink/?LinkId=152665) (<http://go.microsoft.com/fwlink/?LinkId=152665>).  
  
> [!IMPORTANT]
>  You can use the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] Migration Tool to migrate BizTalk projects for LOB adapters to BizTalk projects for WCF-based LOB adapters available with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. You can download the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] Migration Tool from [BizTalk Adapter Pack Migration Tool](http://go.microsoft.com/fwlink/?LinkID=153328) (<http://go.microsoft.com/fwlink/?LinkID=153328>). To know more about migrating LOB adapters to WCF-based LOB adapters included with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], see the [Microsoft BizTalk Adapter 2.0 Migration Whitepaper](http://go.microsoft.com/fwlink/?LinkId=158848) (<http://go.microsoft.com/fwlink/?LinkId=158848>).  
  
## BizTalk Accelerators  
 While BizTalk adapters accommodate sending and receiving documents with a particular protocol, BizTalk accelerators are designed to accommodate the exchange of documents in accordance with a particular industry standard. For a list of the available BizTalk accelerators, see [Microsoft BizTalk Server Accelerators](http://go.microsoft.com/fwlink/?LinkId=103609) (http://go.microsoft.com/fwlink/?LinkId=103609).  
  
##  <a name="BKMK_InternetTrans"></a> Configuring Your Domain When Exposing Transports to the Internet  
 In order to facilitate the sending and receiving of documents between your organization and external trading partners, it may be necessary to expose transports on a public facing site that is accessible from the Internet. Under these circumstances, the following domain configuration is recommended:  
  
- **Employ a perimeter network domain, (also known as a demilitarized zone (DMZ) or screened subnet), to house servers to provide Internet related services for your organization**  
  
   The perimeter network domain should contain servers which house the physical locations where Internet-facing transports route documents between computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and your trading partners. The perimeter network firewall should only open the ports required to allow communications to and from the Internet facing transports. There should be no computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive locations, or Enterprise Single Sign-On server computers in the perimeter network domain. Documents sent/received to/from transports in the perimeter network domain should be routed from the Internet-facing firewall to the firewall protecting the processing domain using Internet Security and Acceleration Server (ISA) Server Web Publishing and Server Publishing. For more information about using ISA Server Web and server publishing, see [Publishing Concepts in ISA Server 2006](http://go.microsoft.com/fwlink/?LinkID=86359) (<http://go.microsoft.com/fwlink/?LinkID=86359>).  
  
  > [!NOTE]  
  >  As an added measure of security, consider using public key infrastructure (PKI) digital certificates for purposes of document encryption and decryption, document signing and verification (non-repudiation) for documents sent to or received from trading partners via Internet facing transports in this domain.  
  
   The following transports are typically used on the perimeter network domain that is accessible from the Internet:  
  
  -   FTP - to receive documents using the FTP protocol  
  
  -   SMTP - to send documents using the SMTP protocol  
  
  -   HTTP - to receive documents using the HTTP protocol  
  
  -   SOAP - to receive documents using SOAP  
  
  -   POP3 - to receive document using the POP3 protocol  
  
- **Employ a processing domain to house servers that contain the BizTalk Server receive and send handlers and a BAM portal server**  
  
   Document flow between the external facing transports in the perimeter domain and BizTalk adapters in the processing domain should be routed through a firewall between these domains. The processing domain should house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ports, receive locations, pipelines, maps, schemas, and assemblies used to receive, route, and send messages. The processing domain should also contain servers for the BAM portal. The number of computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the processing domain will depend on the number of hosts and host instances required to meet the performance needs of your organization.  
  
  > [!IMPORTANT]  
  >  Ensure that you create sufficient isolated host instances in the processing domain to accommodate traffic flowing between the HTTP and SOAP transports in the perimeter domain and the HTTP and SOAP adapters in the processing domain. If a large portion of the document traffic between your organization and your trading partners flows through the HTTP and SOAP transports, there must be sufficient processing bandwidth in the processing domain to handle the document flow.  
  
- **Employ additional domains to provide further layers of isolation and security for your environment**  
  
   These domains should include:  
  
  - A services domain which is trusted by the processing domain and which is needed to process messages successfully. Servers in the services domain typically run BizTalk orchestrations, pipelines, Enterprise Single Sign-On (SSO) services, the Business Rule Engine, and may include other business processes.  
  
  - A data domain for the computers running SQL Server used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
  - A corporate domain for servers and desktop computers to provide services to information workers in your organization.  
  
    For more information about the domain topologies recommended for various [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architectures, see [Sample BizTalk Server Architectures](http://go.microsoft.com/fwlink/?LinkId=155750) (<http://go.microsoft.com/fwlink/?LinkId=155750>).  
  
## High Availability Considerations  
 High availability can be provided for most adapters by running adapter handler host instances on multiple BizTalk servers in a BizTalk group. That way, if one adapter handler host instance fails, another adapter handler host instance is available to continue processing. There are, however, exceptions to doing this. In some cases running multiple adapter handler host instances can cause problems with contention. For example contention problems can occur when running multiple instances of the POP3 and FTP adapters. In these circumstances, high availability can be provided for the adapter by running the adapter handler host instance in a clustered BizTalk host.  
  
 For more information about providing high availability for an adapter handler host instance through host clustering, see [Considerations for Running Adapter Handlers within a Clustered Host](http://go.microsoft.com/fwlink/?LinkID=151284) (http://go.microsoft.com/fwlink/?LinkID=151284). For more information about providing high availability for BizTalk hosts, see [High Availability for BizTalk Hosts](../technical-guides/high-availability-for-biztalk-hosts.md).  
  
## Performance Considerations  
 **SOAP Adapter Performance Considerations**  
  
 For information about optimizing the performance of the SOAP adapter, see [Configuration Parameters that Affect Adapter Performance](http://go.microsoft.com/fwlink/?LinkID=154200) (http://go.microsoft.com/fwlink/?LinkID=154200).  
  
 **MQSeries Adapter Performance Considerations**  
  
 **Disable transaction support and ordered delivery if not required for MQSeries adapter receive locations** When an MQSeries adapter receive location is configured with the **Transaction Supported** option set to **Yes**, or the **Ordered** option set to **Order with Stop**, then each message picked up by the receive location will be processed in the context of an Microsoft Distributed Transaction Coordinator (MSDTC) transaction. Because there is additional overhead incurred when processing messages in the context of an MSDTC transaction, these options should not be enabled if ordered delivery or transaction support is not required for the MQSeries adapter receive location.  
  
## Planning for Ordered Message Delivery  
 Ordered message delivery ensures that messages that are published to the MessageBox database in a given order are delivered to each matching subscriber in the same order. The following considerations apply when implementing ordered delivery of messages:  
  
 **Configuring Ordered Message Delivery**  
  
 Ordered message delivery can be configured in the following places:  
  
- Receive shape in an orchestration  
  
- Receive location for certain adapters  
  
- Send port  
  
  **Ordered Delivery with Existing Transports**  
  
  The protocols underlying certain transports, such as FILE and HTTP, are not consistent with the notion of ordered delivery. However, even with such transports, if the port bound to the transport is marked for ordered delivery, then BizTalk Server enforces ordered delivery by ensuring that the transport does not get the next outbound message until the current one has been successfully sent. To achieve this, BizTalk Server passes each message to the transport's adapter in a single batch and waits until the adapter has successfully deleted the message from the MessageBox database before delivering the next message, in another batch, to the adapter.  
  
  **Ordered Delivery for Custom Adapters**  
  
  For a custom receive adapter to preserve the order of messages when submitting them to BizTalk Server, the adapter must be developed with the following functionality:  
  
- After submitting a batch of messages, your custom receive adapter should wait for the BatchComplete call back from BizTalk Server before submitting the next batch. For more details, see [Interfaces for a Batch-Supported Receive Adapter](http://go.microsoft.com/fwlink/?LinkId=155752) (http://go.microsoft.com/fwlink/?LinkId=155752).  
  
- If a message fails in the pipeline, it should be suspended, preferably as non-resumable. Use the BTS.SuspendAsNonResumable message context property in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to flag the message appropriately.  
  
  > [!NOTE]  
  >  Message order can be broken if a suspended message is later resumed. If you do not want this behavior, suspend failed messages as non-resumable.  
  
  **Conditions for End-to-End Ordered Message Processing**  
  
  To provide end-to-end ordered delivery the following conditions must be met:  
  
- Messages must be received with an adapter that preserves the order of the messages when submitting them to BizTalk Server. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], examples of such adapters are MSMQ and MQSeries. In addition, HTTP or SOAP adapters can be used to submit messages in order, but in that case the HTTP or SOAP client needs to enforce the order by submitting messages one at a time.  
  
- You must subscribe to these messages with a send port that has the **Ordered Delivery** option set to **True**.  
  
- If an orchestration is used to process the messages, only a single instance of the orchestration should be used, the orchestration should be configured to use a sequential convoy, and the **Ordered Delivery** property of the orchestration's receive port should be set to **True**.  
  
## See Also  
 [Planning the Environment for BizTalk Server](../technical-guides/planning-the-environment-for-biztalk-server.md)