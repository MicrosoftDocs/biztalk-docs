---
title: "How to Avoid Throttling Correlated Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bfe47747-01e7-4e2f-bbd5-d5055cea001a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Avoid Throttling Correlated Messages
Messages that are en-queued into BizTalk Server, for example through a receive location or by orchestrations, can be processed in one of the following ways:  
  
- They can activate new instances of subscribers (that is, orchestrations or send ports)  
  
- They can be routed to an existing subscriber instance via correlation. For more information about correlation, see [Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md).  
  
  A lot of developers think about the receive locations for a solution as receiving both activation and correlated messages for the solution through the same port. This is natural as it minimizes the number of addresses that message senders need to keep track of. However, with throttling in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], there can be advantages to thinking about the stream of activation messages and the stream of correlated messages separately when it comes to throttling.  
  
  When both activation and correlation messages arrive through the same receive location, they are subject to the same throttling state because throttling is applied at the host level. As a result, all messages arriving at receive locations in the host will be throttled as a unit. This is not an issue for many scenarios, but there are cases where throttling correlations with activations can result in a type of system deadlock.  
  
## Example  
 For example, let's assume you have a scenario containing an orchestration that receives one activation, uses it to initialize a correlation set, then receives a convoy of 10 additional messages that follow the correlation set. In addition, assume that, under load, a backlog builds up in the spool as the mix of activation and correlation messages arrive that results in throttling the amount of messages that can be received. Unfortunately, the correlation messages are throttled along with the activations, which slows down the completion of orchestrations, causing further backlog and additional throttling. Allowed to continue, this would result in throttling the system down to near zero throughput.  
  
 By splitting the single receive location into two -- one for activations and one for correlations -- and configuring the locations in separate hosts, the database size throttling threshold for the activations can be kept lower than that for correlations, which will result in reduced backlog overall, and keep the messages flowing.  
  
 So, you might be asking: "why can’t I just raise the database size threshold for my single receive location to fix the problem?" The answer is, you can, but it won’t always result in the desired behavior. Throttling is there primarily to protect the system from becoming overloaded. If you raise the thresholds high enough, or turn them off altogether, you will eliminate this protection.  
  
## Recommendation  
 The best practice for scenarios such as the one described above that are sensitive to throttling correlation messages, is to separate the receive locations into separate hosts which can be throttled independently.  
  
 When separate hosts are configured for receive locations, set the database size throttling threshold for the host used by the receive locations to a lower value than the database size throttling threshold for hosts used by orchestrations or correlations.  
  
 If you know that your load will never be higher than the maximum sustainable throughput (MST) for the system, or that throughput peaks are recoverable between peak events, then raising the throttling thresholds will also work, but may not sustain as high a throughput as using separate hosts for activations and correlations.