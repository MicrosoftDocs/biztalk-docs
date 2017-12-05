---
title: "Role of the Base2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f1a695d-5a74-486c-b184-0628d2072aea
caps.latest.revision: 3
---
# Role of the Base
The Base is a part of each Host Integration Server gateway component, such as the local 2.1 node or a link service that provides the operating environment for the core functions of that component. It passes messages between components and provides functions common to all components, such as diagnostic tracing.  
  
 The Base type used with Host Integration Server 3270 emulation programs is DL-BASE. The Host Integration Server DL-BASE supports a single Host Integration Server component or a single user application, and has entry points for initialization, sending messages, receiving messages, and termination.