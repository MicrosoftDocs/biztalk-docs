---
title: "Developing Custom Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44765fbb-b24d-43b6-a40c-d28e319b90a5
caps.latest.revision: 29
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Developing Custom Adapters
To exchange messages with external systems, applications, and entities, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the concept of an adapter. Adapters are COM or [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] components that transfer messages to and from business end. points (such as file systems, databases, and custom business applications) by using various communication protocols. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides native adapters that support various protocols. These include:  
  
- A File adapter that supports sending and receiving messages from a File location  
  
- Adapters for EDI, FTP, HTTP, MSMQ, SMTP, POP3, and SOAP protocols  
  
- An adapter for [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]  
  
  In some cases [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] may need to transport messages to a specific custom application or use a protocol for which a native adapter does not exist. Third-party companies have written adapters to support additional protocols. You may want to determine if there is an adapter for your protocol before deciding to write a custom adapter. For a list of adapters and associated vendors see [http://go.microsoft.com/fwlink/?LinkId=47140](http://go.microsoft.com/fwlink/?LinkId=47140). If you are unable to locate an adapter to support your communication requirements, you can develop your own custom adapter.  
  
  Writing a custom adapter can be a challenging exercise. To simplify this process Microsoft has developed a foundation called the Adapter Framework. You can use this framework as a basis for your development along with sample adapter source code in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK.  
  
  The topics in this section present custom adapter development tips and recommendations.  
  
## In This Section  
  
-   [What Is the Adapter Framework?](../core/what-is-the-adapter-framework.md)  
  
-   [How BizTalk Server Instantiates an Adapter](../core/how-biztalk-server-instantiates-an-adapter.md)  
  
-   [Message Batches](../core/message-batches.md)  
  
-   [Transactional Message Batches](../core/transactional-message-batches.md)  
  
-   [Developing a Receive Adapter](../core/developing-a-receive-adapter.md)  
  
-   [Developing a Send Adapter](../core/developing-a-send-adapter.md)  
  
-   [Instantiating Isolated Adapters](../core/instantiating-isolated-adapters.md)  
  
-   [Adapter Design Issues](../core/adapter-design-issues.md)  
  
-   [How Adapters Handle Large Messages](../core/how-adapters-handle-large-messages.md)  
  
-   [How to Handle Adapter Failures](../core/how-to-handle-adapter-failures.md)  
  
-   [How to Terminate an Adapter](../core/how-to-terminate-an-adapter.md)  
  
-   [How to Design a Performant Adapter](../core/how-to-design-a-performant-adapter.md)  
  
-   [How to Deploy a Custom Adapter](../core/how-to-deploy-a-custom-adapter.md)  
  
-   [How to Test and Debug an Adapter](../core/how-to-test-and-debug-an-adapter.md)  
  
-   [How to Add Adapter Metadata to a BizTalk Project](../core/how-to-add-adapter-metadata-to-a-biztalk-project.md)  
  
-   [Adapter Localization Issues](../core/adapter-localization-issues.md)  
  
-   [Tips for Designing Your Adapter](../core/tips-for-designing-your-adapter.md)  
  
-   [Adapter Design-Time Configuration](../core/adapter-design-time-configuration.md)  
  
## See Also  
 [Developing Custom Components](../core/developing-custom-components.md)