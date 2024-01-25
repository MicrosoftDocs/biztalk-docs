---
description: "Learn more about: Recoverable Interchange Processing"
title: "Recoverable Interchange Processing"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
