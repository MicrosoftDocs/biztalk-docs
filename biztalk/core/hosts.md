---
title: "Hosts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "host instances, servers"
  - "hosts, isolated"
  - "host instances, relationships"
  - "hosts, in-process hosts"
  - "servers, hosts"
  - "hosts, host instances"
  - "hosts, relationships"
  - "In-Process BizTalk Host groups"
  - "hosts, about hosts"
  - "hosts, untrusted"
  - "host instances, hosts"
  - "hosts, servers"
  - "hosts"
  - "servers, host instances"
  - "Isolated Host Users group"
  - "hosts, trusted"
ms.assetid: d96537e0-e679-407a-8870-34a663acfed9
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Hosts
The BizTalk Host object represents a logical set of zero or more runtime processes in which you can deploy services, pipelines, and other artifacts. The Host object also represents a collection of runtime instances (zero or more) where the deployed items physically run.  
  
 After you create a host (a logical container), you can add physical BizTalk servers (host instances) to the host. You cannot add a BizTalk server to the same host more than once. A single host instance can be added to multiple hosts.  
  
 Items—such as adapter handlers, receive locations (including pipelines), and orchestrations—contained in BizTalk hosts can perform the following functions:  
  
- **Receiving**. These items do the initial processing of messages after they are picked up in a receive location. When a host contains a receiving item, such as a receive location or pipeline, it acts as a security boundary, and the message decoding and decrypting occurs in a pipeline within the host.  
  
- **Sending**. These items do the final processing of messages before they are sent out to the send port. When a host contains a sending item, such as a send port or pipeline, the host acts as a security boundary, and the message signing and encryption occurs in a pipeline within the host.  
  
- **Processing**. These items process messages based on the instructions in an orchestration.  
  
  One BizTalk Host can contain items that receive, send, and process messages. It is recommended that you create different hosts for each function to create security boundaries and facilitate management. In particular, it is recommended that you use different hosts for processing and for receive/send, and that you separate trusted and non-trusted items.  
  
  The following figure shows the relationship between servers, hosts, and host instances.  
  
  ![Hosts, host instances, and server relationships](../core/media/ebiz-ops-adm01.gif "ebiz_ops_adm01")  
  Relationship between hosts, host instances, and servers  
  
  For more information about Host Instances, see [Host Instances](../core/host-instances.md).  
  
  Based on the physical configuration and type of adapter hosted, there are two types of hosts: in-process hosts and isolated hosts.  
  
## In-process Hosts  
 In-process hosts represent service instances that an administrator creates, deletes, and fully controls with Windows Management Instrumentation (WMI) and the BizTalk Administration Console.  
  
 In-process hosts have the following characteristics:  
  
- You can enlist any orchestration into an in-process host.  
  
- An in-process host can host any send handler.  
  
- An in-process host can host any of the receive handlers except for SOAP and HTTP:  
  
  -   FILE  
  
  -   FTP  
  
  -   MQSeries  
  
  -   MSMQ  
  
  -   POP3  
  
  -   SQL  
  
  -   Windows SharePoint Services  
  
- The first in-process host you create in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment is the **default host** and you cannot delete it. The BizTalk Message Queuing adapter uses the default host for static handler configuration. Adding an adapter automatically creates receive and send ports for the default host.  
  
## Isolated Hosts  
 Isolated hosts represent service instances that a solutions developer programmatically creates, deletes, and controls. An administrator uses WMI and the BizTalk Administration Console to configure these hosts (for example, to configure the host service account and authentication trust).  
  
 Isolated hosts primarily host adapters that must run outside of the normal BizTalk Server runtime process. For example, you use isolated hosts to host adapters for external processes such as ISAPI extensions and ASP.NET.  
  
 Isolated hosts have the following characteristics:  
  
-   You cannot enlist orchestrations into an isolated host.  
  
-   An isolated host cannot host send handlers.  
  
-   An isolated host can host only the receive handlers associated with HTTP/S and SOAP adapters (the isolated-type adapters).  
  
-   An isolated host cannot host tracking.  
  
-   An isolated host cannot be the default host.  
  
-   The status of an isolated host is always **Status Unavailable**. BizTalk Server does not access the status information for external processes.  
  
> [!NOTE]
>  Host instances can share the same service account as long as they share the same security configuration (authentication trust).  
  
## Trusted and Untrusted Hosts  
 BizTalk Server enables hosts identified as authentication trusted to indicate that the sender of a message that the trusted host is queuing to the MessageBox database is an entity other than the trusted host itself. The primary purposes of authentication trust are to enable pipelines to resolve to a Product ID (PID) and pass that PID along to consuming services for use in authorization and outbound party resolution, and to enable the transmission of the sender Windows Security ID (SSID) along to consuming services for use in orchestration action authorization.  
  
## See Also  
 [Host Instances](../core/host-instances.md)   
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)  
 [Entities](../core/entities.md)