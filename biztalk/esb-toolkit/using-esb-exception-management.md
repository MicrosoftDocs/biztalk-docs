---
title: "Using ESB Exception Management | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: de6ce411-2d34-4fd8-9644-6fbc9cec266d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using ESB Exception Management
Errors and exceptions can occur in a range of contexts and during a number of different processing stages in an ESB. This section provides information about handling exceptions and describes how you can publish details through the ESB Management Portal.  
  
## Overview  
 There are many ways to handle exceptions in a [!INCLUDE[prague](../includes/prague-md.md)] solution, including using frameworks such as the Enterprise Library. However, when developing with ESB and BizTalk Server, you are working in a message-based environment. Everything in a BizTalk solution is message-oriented, and BizTalk developers think in a message-oriented way. Therefore, the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] implements a message-oriented approach to exception handling.  
  
 The ESB Exception Management Framework follows a design pattern that provides a flexible approach to exception monitoring and enables error responses to originate from outside of the solution—perhaps at business-unit level.  
  
 The following topics discuss the ESB Exception Management Framework in more detail:  
  
-   [Design of the ESB Exception Management Framework](../esb-toolkit/design-of-the-esb-exception-management-framework.md)  
  
-   [The Components of the Exception Management Framework](../esb-toolkit/the-components-of-the-exception-management-framework.md)  
  
-   [Using the Exception Management Framework](../esb-toolkit/using-the-exception-management-framework.md)  
  
-   [Creating Custom Exception Handlers](../esb-toolkit/creating-custom-exception-handlers.md)