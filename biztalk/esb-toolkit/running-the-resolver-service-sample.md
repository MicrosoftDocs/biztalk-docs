---
title: "Running the Resolver Service Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b4bf0b21-6aa0-4524-9e63-93a172845d4a
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Running the Resolver Service Sample
The Resolver Service sample demonstrates the following scenarios:  

- Resolve a service endpoint URI from UDDI3 using a binding key  

- Resolve a service endpoint URI from UDDI3 using a categorization search  

- Resolve a transformation (BizTalk Map type) using a STATIC resolver  

- Resolve a service endpoint URI using a STATIC resolver  

- Resolve a service endpoint URI using an XPath expression  

- Resolve an itinerary using a static ITINERARY resolver  

- Resolve an itinerary using an ITINERARY-STATIC (Unity) resolver  

- Resolve an itinerary using BRE (BRI Resolver)  

- Resolve an Itinerary using BRE (BRI Resolver) with the Message  

- Resolve a service endpoint URI using BRE  

- Resolve a transformation using BRE  

  **To run all the resolution scenarios using the ASMX implementation of the Resolver service**  

1. If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.  

2. In Windows Explorer, open the \Source\Samples\ResolverService folder, and then double-click the file RunTestClient_ASMX.cmd.  

3. Open the \Source\Samples\ResolverService\Output folder, and then open the result files, which correspond to the resolution requests listed earlier.  

   **To run all the resolution scenarios using the WCF implementation of the Resolver service**  

4. If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.  

5. In Windows Explorer, open the \Source\Samples\ResolverService folder, and then double-click the file RunTestClient_WCF.cmd.  

6. Open the \Source\Samples\ResolverService\Output folder, and then open the result files, which correspond to the resolution requests listed earlier.
