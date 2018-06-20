---
title: "Creating a PeopleSoft HTTP Host and Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HTTP port"
  - "HTTP host"
ms.assetid: 3e1ce5fd-32ee-409f-b4c8-f2bc68470f17
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating a PeopleSoft HTTP Host and Port
The Message publication architecture in PeopleSoft is known as Integration Broker. The main components of Integration Broker are as follows:  
  
- Gateway  
  
- Publishing node  
  
- Subscriber node  
  
  All three work together to publish a message to a URL for an HTTP listener. You must set the Publishing node. PeopleSoft has a default publishing node, also known as local message node. You must activate the node and the transactions for the publishing node. You must set the Subscription node with the type as external node, and then activate the node and the transactions. For this node, you also set the type to be HTTP and set the connection information.  
  
  You use PeopleSoft Integration Broker to create a PeopleSoft HTTP Host and Port where PeopleSoft sends events. You make sure that the message is active and routed by using the procedure in [How to Verify Activity Status of a Message](../core/how-to-verify-activity-status-of-a-message.md).  
  
## In This Section  
  
-   [How to Verify Activity Status of a Message](../core/how-to-verify-activity-status-of-a-message.md)  
  
-   [How to Configure the Integration Gateway and HTTP Output Connector](../core/how-to-configure-the-integration-gateway-and-http-output-connector.md)  
  
-   [How to Create a New Gateway Node](../core/how-to-create-a-new-gateway-node.md)  
  
-   [How to Add a Transaction](../core/how-to-add-a-transaction.md)  
  
-   [How to Test the HTTP Node](../core/how-to-test-the-http-node.md)