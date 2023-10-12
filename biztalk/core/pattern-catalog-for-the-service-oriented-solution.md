---
description: "Learn more about: Pattern Catalog for the Service Oriented Solution"
title: "Pattern Catalog for the Service Oriented Solution"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Pattern Catalog for the Service Oriented Solution
The patterns in the service oriented solution include patterns of BizTalk Server-specific programming practices, as well as the enterprise integration patterns in preceding sections. The list in this section includes both kinds of patterns.  
  
## Pattern Types  
 Entries described in the following topics briefly describe the pattern and point to other topics that describe how the solution uses the pattern. In the case of general patterns, such as a filter, entries point to more general topics.  
  
### Aggregation Pattern  
 Aggregation is the pattern of receiving information from multiple sources and consolidating it into a single message. The service oriented solution combines credit information from three different sources into a single response. You can do aggregation several different ways, depending on the nature of the solution you're writing. In some cases, you may need to wait for all responses. In other cases, such as in loan quotes, you may be willing to forego getting a response so long as you have some minimum number. The service oriented solution waits until it has all three responses because it requires all three in order to have a complete credit report to return. For more information, see [Translating the Patterns of the Service Oriented Solution](../core/translating-the-patterns-of-the-service-oriented-solution.md).  
  
### Calling Pipelines from Code Pattern  
 You can now call pipelines from your code and orchestrations. This allows the re-use of pipelines and helps maintain the decoupling of an orchestration from the pipeline stages. For more information, see [Using Pipelines from the Service Oriented Solution](../core/using-pipelines-from-the-service-oriented-solution.md).  
  
### Caching Pattern  
 Caching is a general strategy of storing information rather than retrieving it from a data store every time it is requested. Retrieving reference or configuration data from the Enterprise Single Sign-On system proved to be a limiting factor in the solution. The solution caches the information and periodically refreshes the cache. For more information, see [Using SSO Efficiently in the Service Oriented Solution](../core/using-sso-efficiently-in-the-service-oriented-solution.md). The Business Process Management solution also caches the SSO information, though it uses a slightly different process. For more information, see [Using SSO Efficiently in the Business Process Management Solution](../core/using-sso-efficiently-in-the-business-process-management-solution.md).  
  
### Content-Based Routing Pattern  
 In enterprise integration patterns, content-based routing is more broadly conceived than in BizTalk. In enterprise integration patterns, content-based routing is determining the recipient of a message based on the some part of the content of the message. The service oriented solution uses a very simple form of content-based routing—a single decision shape in an orchestration sends the message one of two places. For more information, see "Translating the Components into Orchestration Shapes" in [Translating the Patterns of the Service Oriented Solution](../core/translating-the-patterns-of-the-service-oriented-solution.md).  
  
### Filter Pattern  
 The filter pattern selects messages meeting particular criteria for processing. In BizTalk Server, the filter pattern almost always becomes a filter expression on a port. For more information about filters on ports, see [Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md).  
  
### Inline Invocation of Back-end Processes Pattern  
 The inline version of the solution uses inline invocation of the back-end processes through custom assemblies. This has the benefit of greatly improved performance. It comes at the cost, however, of tightly coupling the orchestration to the transport protocol. For more information, see [Inlining Back-end Invocation](../core/inlining-back-end-invocation.md).  
  
### Recipient List Pattern  
 In an abstract sense, the service oriented solution implements a recipient list in that it sends messages to three different systems. In practical terms, the deployed application determines the recipients by mapping the logical ports to specific locations. In the case of the inline version of the application, the connections are made through the configuration information in SSO. For more information, see [Translating the Patterns of the Service Oriented Solution](../core/translating-the-patterns-of-the-service-oriented-solution.md).  
  
### Service Interface Pattern  
 The service oriented solution presents itself as a Web service, only one of many ways a service may be done. For more information about using orchestrations as Web services, see [Using Web Services](../core/using-web-services.md).  
  
### Translator Pattern  
 The enterprise pattern of a translator—that is, the conversion of a message from one form to another form—most often translates into a BizTalk Server map. For general information about BizTalk Server maps, see [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md).  
  
## See Also  
 [Patterns in the Service Oriented Solution](../core/patterns-in-the-service-oriented-solution.md)
