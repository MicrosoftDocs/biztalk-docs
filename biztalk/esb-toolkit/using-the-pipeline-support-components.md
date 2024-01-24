---
description: "Learn more about: Using the Pipeline Support Components"
title: "Using the Pipeline Support Components"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Using the Pipeline Support Components
The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes the following pipeline components:  
  
-   **ESB Itinerary Selector**. You can use this component on the receive side (in a receive pipeline) to select a server-side itinerary for a message to follow. For more information, see [The ESB Itinerary Selector Component](../esb-toolkit/the-esb-itinerary-selector-component.md).  
  
-   **ESB Itinerary**. You can use this component on the receive side (in a receive pipeline) to promote ESB metadata properties from SOAP headers into the message context. For more information, see [The ESB Itinerary Component](../esb-toolkit/the-esb-itinerary-component.md).  
  
-   **ESB Itinerary Forwarder**. For more information, see [The ESB Itinerary Forwarder Component](../esb-toolkit/the-esb-itinerary-forwarder-component.md).  
  
-   **ESB Itinerary Cache**. You can use this component to cache itineraries and reapply them to response messages received in Solicit-Response send ports. For more information, see [The ESB Itinerary Component](../esb-toolkit/the-esb-itinerary-component.md).  
  
-   **ESB JMS Decoder**. You can use this component on the receive side (in a receive location) of an orchestration or a send port to parse out IBM JMS (MQRFH2) headers and preserve them as context properties. You can then access these context properties and modify them in the same way as any other BizTalk context properties. For more information, see [The ESB JMS Encoder and Decoder Components](../esb-toolkit/the-esb-jms-encoder-and-decoder-components.md).  
  
-   **ESB JMS Encoder**. You can use this component in a send port to write IBM JMS (MQRFH2) headers to messages. For more information, see [The ESB JMS Encoder and Decoder Components](../esb-toolkit/the-esb-jms-encoder-and-decoder-components.md).  
  
-   **ESB Add Namespace**. You can use this component in either a receive location or a send port to add namespaces to XML documents. For more information, see [The ESB Add Namespace and Remove Namespace Components](../esb-toolkit/the-esb-add-namespace-and-remove-namespace-components.md).  
  
-   **ESB Remove Namespace**. You can use this component in either a receive location or a send port to remove namespaces from XML documents. For more information, see [The ESB Add Namespace and Remove Namespace Components](../esb-toolkit/the-esb-add-namespace-and-remove-namespace-components.md).  
  
-   **ESB Exception Encoder**. You can use this component to send fault messages to the file system, Microsoft InfoPath, or Microsoft SharePoint. This component is part of the ESB exception handling mechanism, and it normalizes and enriches all exceptions processed by a send port. The component serializes exception information (including embedded persisted messages and context properties) into a canonical format so that all contained messages and the exception itself are available.  
  
-   **ESB Transform**. You can use this component to transform message from one format to another by specifying BizTalk map.  
  
-   **ESB BAM Tracker**. You can use this component to intercept the fault message emitted from the ESB Exception Encoder and insert the data in the message into the BAM Primary Import table (using the BAM Event Stream in the pipeline). This component is part of the ESB exception handling mechanism.  
  
-   **ESB Dispatcher**. You can use this component in a receive location (inbound pipeline) to dynamically set endpoint location properties for outbound messages. You can also use this component in the send pipeline to execute itinerary messaging services. For more information, see [The ESB Dispatcher Component](../esb-toolkit/the-esb-dispatcher-component.md).  
  
-   **ESB Dispatcher Disassemble**. You can use this component in a receive location (inbound pipeline) to dynamically set endpoint location properties for outbound messages. The behavior of this component is similar to the ESB Dispatcher component, except that it transforms the result message (if you specify a value for the **MapName** property). The message passes through the XML Disassembler, which promotes properties and message types. The ESB Dispatcher Disassemble component also supports batched dispatch of multiple messages to different endpoints. For more information, see [The ESB Dispatcher Disassemble Component](../esb-toolkit/the-esb-dispatcher-disassemble-component.md).
