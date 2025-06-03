---
description: "Learn more about: Instrumentation Best Practices for High Performance BizTalk Solutions"
title: "Instrumentation Best Practices for High Performance BizTalk Solutions"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: best-practice
---
# Instrumentation Best Practices for High Performance BizTalk Solutions

 **Published:** November 2010

 **Author:** Valery Mizonov, Microsoft Corporation

 **Reviewed By:**

- Mark Simms, Microsoft Corporation

- Jayanthi Sampathkumar, Microsoft Corporation

- Krish Srinivasan, Microsoft Corporation

  **Applies To:** Microsoft BizTalk Server

  **Summary:** The traditional ways of instrumenting BizTalk solutions may not always be the most effective from a performance standpoint. The commonly used instrumentation and tracing components leveraging the Win32 Debugging APIs may introduce a potential bottleneck and become responsible for performance degradations in multi-threaded BizTalk applications running under stress.

  From the other side, source code instrumentation delivers a great degree of visibility into the application behavior and helps reduce the overall troubleshooting efforts. Consequently, a fundamentally new approach to instrumenting high performance BizTalk solutions has become crucially important to enable collecting the rich and detailed diagnostic information in a non-intrusive manner with virtually no overhead and no impact on the application performance.

  The [Windows Server AppFabric Customer Advisory Team](/archive/blogs/appfabriccat/) at Microsoft aimed to provide the community with validated best practices to help BizTalk developers enrich their solutions with the high-performance instrumentation internally adopted by many Microsoft products. These best practices have been reflected in the form of a reusable framework which BizTalk developers can easily plug in and adopt in their own implementations.
