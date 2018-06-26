---
title: "Tutorials to learn the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99002b01-da8a-483e-ada3-1ffbe9cd7357
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tutorials to learn the WCF LOB Adapter SDK
The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] tutorials contain information about how you can use [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] to develop feature-rich line of business adapters to facilitate enterprise application integration within your enterprise. By using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], the operations and data you expose can be consumed by any application that can consume a WCF binding, including [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
 The tutorials contain simple examples built around a set of predefined operations. You do not need an actual line of business system available to complete these tutorials. However, details provided in the tutorials can be applied to your adapter development needs, from understanding metadata to writing outbound handlers and beyond.  

> [!TIP]
> The completed Echo Adapter is included with your BizTalk installation files at `\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples` or `\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`.
  
 Use the following tutorials to learn how to use key parts of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]:  
  
- [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md). Provides step-by-step instructions for creating an adapter that exposes string operations from a set of predefined methods that act as the line of business system. The adapter provides an implementation for many of the common handlers in the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] including search, browse, inbound and outbound operations. At the successful completion of this tutorial, you will have a functional adapter.  
  
- [Tutorial 2: Consume the Echo Adapter from .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md). Provides step-by-step instructions for consuming the Echo Adapter developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) from a .NET project. You will add an adapter service reference to a new project, and provide code to test the inbound and outbound operations of the Echo Adapter.  
  
- [Tutorial 3: Hosting the Echo Adapter in IIS](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md). Provides step-by-step instructions for hosting the Echo Adapter developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) in the Internet Information Services (IIS) process. You will also use svcutil.exe (ServiceModel Metadata Utility) to create a simple client application to consume the EchoString operation of the hosted adapter.  
  
  These tutorials provide a structured approach to understanding some of the key features of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. They can be completed with no knowledge of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] or [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]. However, you will learn more if you understand the concepts behind adapter design, and understand how adapter design is facilitated in the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. For more information, see:  
  
- [Common Developer Tasks for the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/common-developer-tasks-for-the-wcf-lob-adapter-sdk.md)  
  
- [Key Components of the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/key-components-of-the-wcf-lob-adapter-sdk.md)  
  
  Before you begin these tutorials, you should review the requirements in [Before You Begin the Tutorials](../../core/before-you-begin-the-tutorial.md).  
  
 
## In This Section  
  
-   [Before You Begin the Tutorials](../../core/before-you-begin-the-tutorial.md)  
  
-   [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)  
  
-   [Tutorial 2: Consume the Echo Adapter from .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)  
  
-   [Tutorial 3: Hosting the Echo Adapter in IIS](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)  
  
## See Also  
 [Getting started with BizTalk Server](../../core/getting-started-with-biztalk-server.md)