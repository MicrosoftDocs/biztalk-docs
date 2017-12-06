---
title: "Role of the Base1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5bb7a62-0e26-42ec-9b6f-ad67131b9b64
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Role of the Base
The Base is a part of each Host Integration Server gateway component, such as the local 2.1 node or a link service that provides the operating environment for the core functions of that component. It passes messages between components and provides functions common to all components, such as diagnostic tracing.  
  
 The Base type used with Host Integration Server 3270 emulation programs is DL-BASE. The Host Integration Server DL-BASE supports a single Host Integration Server component or a single user application, and has entry points for initialization, sending messages, receiving messages, and termination.