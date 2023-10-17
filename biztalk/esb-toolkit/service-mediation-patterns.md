---
title: Service Mediation Patterns | Microsoft Docs
description: "Details the two types of service mediation patterns: service mediation patterns and request-response patterns."
ms.custom: ""
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: article
ms.assetid: cfda54db-75fa-4bc2-9f48-11d8b3cde65b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
---
# Service Mediation Patterns

## VETO/VETRO

 The VETRO pattern is a common composite pattern that combines multiple actions taken on a message when it is received. The term VETRO is an acronym that stands for Validate, Enrich, Transform, Route, Operate. In the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], these actions can be handled as individual stages in the pipeline associated with the receive location. For more information about how each of these stages can be implemented, see Key Scenarios and Development Tasks.

## Request-Response

 The Request-Response pattern defines a solution in which a service or party sends a request message and expects a reply message in return from the destination service. For a detailed description of this pattern, see [Request-Reply](https://go.microsoft.com/fwlink/?LinkId=186849) ([https://go.microsoft.com/fwlink/?LinkId=186849](https://go.microsoft.com/fwlink/?LinkId=186849)) on the Enterprise Integration Patterns site.

 For more information about how to implement this pattern, see the following resources:

-   [How to: Transform a Message and Route to a Service Endpoint Using a Request-Response Message Exchange Pattern](../esb-toolkit/transform-message-and-route-to-service-endpoint-using-request-response-message.md)

-   [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)