---
title: "Linking 3270 Client Applications1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ed0878f9-f74d-4894-a3db-92a8a43af7c2
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Linking 3270 Client Applications
This topic describes how to link 3270 client applications using different platforms.  
  
 The SNACLI.LIB library must be linked with the application.  
  
 The DMOD is implemented as a DLL. SNACLI.LIB contains import definitions for the APIs in the DLL, and some global variables required for the logging and tracing macros.  
  
 It is possible to create a DLL that is dynamically loaded when the user starts a session for an LU. In this case, to make the log and trace macros available, the application structure needs to be as shown in the following figure.  
  
 ![](../core/media/32708a.gif "32708a")  
Application Structure