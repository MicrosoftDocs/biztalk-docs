---
description: "Learn more about: Translating the Patterns of the Service Oriented Solution"
title: "Translating the Patterns of the Service Oriented Solution"
ms.custom: "devx-track-javaee-websphere"
ms.date: "12/30/2022"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Translating the Patterns of the Service Oriented Solution
This section describes how the solution translates the pattern diagram into BizTalk Server artifacts.  
  
 ![Service&#45;Oriented Solution Patterns](../core/media/service-oriented-solution-patterns.gif "Service_Oriented_Solution_Patterns")  
  
## Connections and Completeness Conditions  
 We can pretty much start anywhere with translating the patterns into BizTalk Server components. However, the connections among the components are, in effect, the infrastructure for the components so that it seems a good place to start. Also, in the case of the aggregator pattern, we need to think about what will tell it that it has all of the information it needs. This affects both its connections to other components as well as its design.  
  
 The solution needs to provide a convenient and consistent way of being used. The service interface specifies how other applications can use it. Because the solution needs to communicate with a legacy application using IBM WebSphere MQ, IBM WebSphere MQ needs to be part of the service interface. However, for newer applications, a Web service interface seems an obvious choice. A Web service interface provides maximum flexibility for other applications using the service. Here, we can use the flexibility of BizTalk Server to have a dual service interface. For information about exposing orchestrations as Web services, see [How to Map Orchestrations to Web Services](../core/how-to-map-orchestrations-to-web-services.md).  
  
 The other connections are those between the service interface and the recipient list, between the recipient list and the back-end applications, and among the back-end applications, aggregator, and the service interface.  
  
 If the connection to the recipient list is synchronous, the solution does not need to use correlations to ensure all messages to the recipient list are sent and received. The connections between the back-end applications and the aggregator can be synchronous for the same reasons. The aggregator needs the responses from all three of the back-end applications to complete the query response. Response times should be short so that synchronous connections are appropriate and simplify the solution.  
  
 In the aggregator pattern, there is usually a completeness condition. In cases where there are multiple back-end servers and response times are slow, the completeness condition might be, for example, receiving at least one response in a given time period. This service-oriented solution requires all three responses in order to construct the final message. Thus, here, the completeness condition is receiving all three responses.  
  
> [!NOTE]
>  When receiving requests through IBM WebSphere MQ, the solution adds a correlation identifier by copying the **MQMD_MsgId** value to the **MQMD_CorrelId** of the response message. This is part of the standard way of using the MQSeries adapter in request-reply to avoid a possible race condition. For more information, see [Correlating Messages Using Request-Reply](../core/correlating-messages-using-request-reply.md).  
  
## Determining Orchestration Boundaries  
 The solution must allow for requests from an IBM WebSphere MQ queue as well as through the Web service interface. Putting the service interface into one orchestration, the IBM WebSphere MQ input into another, and the bulk of the processing into a third keeps the external communication separated from the processing.  
  
## Translating the Components into Orchestration Shapes  
 The patterns to translate into shapes will, in the final solution, be in a single orchestration. There are numerous ways to create a content-based router in BizTalk Server, including creating MessageBox subscriptions. In the solution, the routing uses MessageBox subscriptions. An expression shape evaluates whether or not the message includes values for the required fields. A decision shape evaluates the variable set in the expression shape and selects the path through the orchestration.  
  
 The **CustomerService** orchestration uses the parallel shape to send messages to the backend applications and receive responses simultaneously. It does not have to wait on one application finishing before making the next request. If the number of applications were to change frequently, or if the connections to the applications were unreliable, then the orchestration would need to translate the pattern differently.  
  
 In the solution the aggregator must combine elements from three response messages. Using the parallel shape ensures that the communication with the back-end systems is parallel. And, because the shape does not terminate until it receives all responses or a timeout, the aggregator will always know when it can proceed. The orchestration uses a transform shape that maps elements from the three backend response messages and the original request message to elements in the response message.  
  
> [!NOTE]
>  The communications with the back-end systems may also time out. You can set the time-out period by enclosing the **Receive** shape in a **Scope** shape and setting the **Timeout** property of the scope.  
  
 For a complete list of orchestration shapes, see [Orchestration Shapes](../core/orchestration-shapes.md).  
  
## See Also  
 [Patterns in the Service Oriented Solution](../core/patterns-in-the-service-oriented-solution.md)   
 [Components of the Service Oriented Solution](../core/components-of-the-service-oriented-solution.md)
