---
title: "Tips for Designing Your Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bb60988-4e48-4654-9cf4-512dd7c97239
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tips for Designing Your Adapter
This section contains hints and tips that adapter developers have learned while designing adapters.  
  
## Handler Properties Should Be Strings if Used as Default Configurations  
 It seems attractive to use the properties on the XSD-generated handler property sheet as defaults for their **Location** properties because if the value is not set in **Location** the runtime automatically uses the value set in the handler. But there are several issues that make this less useful.  
  
 The problem comes with not knowing whether the value presented to the runtime is to be overridden or not. The typical way of doing this is to have some notion of NULL defined for values and then run a test against that value. The problem when using the XSD-based property sheets in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is that NULL is only supported for strings. Even if you want your adapter to have default settings through the use of this NULL test and are willing to restrict the adapter to string types, it is still exposed to a very odd piece of user interface.  
  
 The XSD-generated property sheets only support the setting of a property back to NULL by right-clicking the property, at which point a **nullify?** context menu appears and the property can be set to NULL. There is no visual feedback as to whether a property is NULL.  
  
## Considerations for Implementing Schema Generation Wizards  
 Programmers like to code against strongly typed object models. Manipulating XML in code can at first seem awkward and prone to error. But some tricks and smart use of the support offered by the .NET Framework can dramatically simplify matters.  
  
#### Do not create XML documents with string concatenation  
 One of the worst mistakes to make with XML is to try and generate it from string concatenation and print statements in memory. This consumes large amounts of CPU time and memory. Even for the most trivial XML snippet, it is easier to use a tool like XmlWriter or the Document Object Model (DOM). If you are using XmlWriter, do not use the raw write capability, because the writer loses the state of the document.  
  
 At run time, XmlWriter is preferred over the XML DOM because of high memory consumption issues associated with the DOM. However, at configuration or design time this will most likely not be an issue. Using the DOM facilitates the use of XPATH queries, which can be a useful additional tool.  
  
#### Consider defining the skeleton of your XML document as a resource  
 If you are generating a large XML document from a design tool and that generated document always follows the same basic structure, consider placing the whole skeletal XML file as a resource in the project to allow making changes when you need to edit it.  
  
 Load the code into a DOM and then add the necessary flesh to the bones of the document by using XPATH to pick out the node you want to add it to. In this case, you are creating a Web Services Description Language (WSDL) file. The wizard stores the skeletal WSDL file in a resource and adds the generated XML Schema Definition (XSD) child parts. It uses selectNode with an xpath to find the right parent. This is user interface code, so performance is not an issue, and the resulting implementation is clean, robust, and maintainable.  
  
## Consider Placing Processing Steps in the BizTalk Pipeline  
 In general the adapters built at Microsoft move message format-based processing out of the adapter and into the BizTalk pipeline. A good example is an adapter to a structured but non-XML data source.  
  
 In this case, the adapter only gets the data and the BizTalk pipeline is used to parse it and convert it into an XML equivalent. The benefit is that the pipeline component itself becomes a reusable piece of the architecture.  
  
## Make Adapter Behavior Configurable  
 One of the lessons learned from the MQSeries adapter beta program was that not all customers were happy with the same behavior. This was especially true when it came to handling errors and ordering. The solution was to make the behavior configurable. You can specify whether the adapter is to support ordering, whether failures are moved to the Suspended queue, or whether they cause the adapter to stop processing and disable itself. Making such behaviors configurable can significantly simplify customers' lives when they would need to write complex orchestrations or scripts external to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to achieve the same result.  
  
## Support Correlation with Message Queues  
 Many messaging platforms support the notion of a correlation ID in the message header to support an application-level request-response scenario. Examples include MQSeries, MSMQ, and SQL Service Broker. It would seem attractive to map the request-response pattern of the external messaging system to a send-response adapter in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. However this does not make sense because of where the transactions live. Specifically, a send to the external messaging system requires a transactional commit before the other end of the queue sees the data. The receive must also be a separate transaction.  
  
 The solution in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is to:  
  
- Use correlation sets in orchestration  
  
- Configure two separate ports: one for the send and one for the receive  
  
  In a simple case the orchestration specifies the correlation ID that is associated with the message by the adapter. This is passed to the adapter as a context property on the message. In a more complex case, the scenario calls for the external messaging system to allocate the ID. In this case it can be passed back from the send port to the orchestration with a response message. This response message is just to pass back the ID and is not the true message response.  
  
> [!NOTE]
>  There is a race condition in the orchestration engine such that the true response to the message could win against the ID response from the send. This race condition must be handled in the orchestration itself.