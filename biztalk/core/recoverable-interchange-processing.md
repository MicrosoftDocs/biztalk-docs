---
title: "Recoverable Interchange Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interchange processing [Messaging Engine], modes"
  - "parties, party resolution"
  - "Messaging Engine, examples"
  - "messages, interchange modes"
  - "interchange processing [Messaging Engine], examples"
  - "Messaging Engine, Recoverable Interchange Processing property"
  - "Messaging Engine, failures"
  - "interchange processing [Messaging Engine], party resolution"
  - "Messaging Engine, interchange processing"
  - "disassembly stage, pipelines"
  - "Recoverable Interchange Processing property"
  - "Messaging Engine, interchange modes"
  - "receive pipelines, disassembly stage"
  - "interchange processing [Messaging Engine], failures"
  - "interchange processing [Messaging Engine], restrictions"
  - "System.Xml.XmlReader"
  - "interchange modes [Messaging Engine]"
ms.assetid: d9e366fe-b2a0-4f1a-b6b9-1264717e4731
caps.latest.revision: 30
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Recoverable Interchange Processing
This section discusses **recoverable interchange processing** feature, which allows an interchange to be processed completely even if one or more messages in the interchange fail at the following stages/phases:  
  
- Disassembly stage of a receive pipeline  
  
- XML validation stage of a receive pipeline  
  
- Map execution phase of a receive port  
  
  Recoverable interchange processing is motivated by the need to support successful processing of a single interchange that contains multiple identifiable messages so that valid messages are propagated through the messaging pathway and invalid messages are suspended. With standard interchange processing, the existence of any invalid message in a given interchange causes the entire interchange to be suspended even if it contains one or more valid messages.  
  
## In This Section  
  
-   [Disassembly Stage (Recoverable Interchange Processing)](../core/disassembly-stage-recoverable-interchange-processing.md)  
  
-   [XML Validation Stage (Recoverable Interchange Processing)](../core/xml-validation-stage-recoverable-interchange-processing.md)  
  
-   [Mapping Phase (Recoverable Interchange Processing)](../core/mapping-phase-recoverable-interchange-processing.md)