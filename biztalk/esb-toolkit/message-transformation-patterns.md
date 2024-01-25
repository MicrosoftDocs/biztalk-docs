---
description: "Learn more about: Message Transformation Patterns"
title: "Message Transformation Patterns"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Message Transformation Patterns
Message transformation patterns define proven guidelines for transforming messages for additional processing or to match the expected document format of the service to which the message will be sent. A message may require transformation because the structure of the received message is not in the expected standard or because the message must be converted from a non-standard format to XML.

## Message Translator
 The Message Translator pattern defines a solution for communication between systems that use incompatible data formats. For example, a client application may send a flat file request message that must be converted to XML before additional processing can occur. For a detailed description of this pattern, see [Message Translator](https://go.microsoft.com/fwlink/?LinkId=186845) ([https://go.microsoft.com/fwlink/?LinkId=186845](https://go.microsoft.com/fwlink/?LinkId=186845)) on the Enterprise Integration Patterns site.

 The implementation of this pattern in Itinerary Designer is a combination of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] transformation service and a single resolver. The itinerary transformation service is responsible for transforming a message using resolver properties that define the artifacts required for transformation. The resolver implementation is responsible for providing transformation settings, which can be defined statically or dynamically, depending on the resolver configuration.

 For an example implementation of the Message Translator pattern, see the following resources:

-   [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)

-   [How to: Transform a Message and Route to a Service Endpoint Using a Request-Response Message Exchange Pattern](../esb-toolkit/transform-message-and-route-to-service-endpoint-using-request-response-message.md)

## Normalizer
 The Normalizer pattern is an extension of the Data Model Transformation pattern. This pattern defines a solution in which messages received from multiple sources are semantically equivalent, but the messages arrive in different formats. For a detailed description of this pattern, see [Normalizer](https://go.microsoft.com/fwlink/?LinkId=186847) ([https://go.microsoft.com/fwlink/?LinkId=186847](https://go.microsoft.com/fwlink/?LinkId=186847)) on the Enterprise Integration Patterns site.

 The implementation of this pattern in Itinerary Designer is a combination of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] transformation service and a single resolver. The itinerary transformation service is responsible for transforming a message using resolver properties that define the artifacts required for transformation. The resolver implementation is responsible for dynamically resolving the appropriate Microsoft BizTalk map for a specified type of message.

 For an example implementation of the Normalizer pattern, see the [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).

## Content Enricher
 The Content Enricher pattern defines a solution in which a received message may not include all the data required for the target system to appropriately process the message. For example, the sending service may include a ZIP code without a redundant state code, but the receiving service expects a message that includes both a state code and a ZIP code; additional data is required before the receiving service can process the received message. For a detailed description of this pattern, see [Content Enricher](https://go.microsoft.com/fwlink/?LinkId=186848) ([https://go.microsoft.com/fwlink/?LinkId=186848](https://go.microsoft.com/fwlink/?LinkId=186848)) on the Enterprise Integration Patterns site.

 For an example implementation of the Content Enricher pattern, see the [Installing and Running the Message Enrichment Sample](../esb-toolkit/installing-and-running-the-message-enrichment-sample.md) application.
