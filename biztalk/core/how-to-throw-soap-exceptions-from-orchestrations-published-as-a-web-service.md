---
title: "How to Throw SOAP Exceptions from Orchestrations Published as a Web Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "errors, SOAP exceptions"
  - "orchestrations, SOAP errors"
  - "Web services, orchestrations"
ms.assetid: e1c7cd74-d1c8-4b9d-a418-4601b1f040d7
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Throw SOAP Exceptions from Orchestrations Published as a Web Service
You can return a SOAP exception from an orchestration that you have published as a Web service. You add a fault message to your SOAP port and send the fault message instead of the response.  
  
### To throw a SOAP exception from an orchestration published as a Web service  
  
1. Add a fault message to the SOAP port type. The message type for the fault message can be any XML Schema (XSD) compliant schema or simple type.  
  
   > [!NOTE]
   >  To return a string as a **SoapException** with error information, you can use the simple type string as the fault message type.  
  
2. In your orchestration, create the fault message.  
  
3. Use the **Send** shape to link to the fault operation in the SOAP port that corresponds to the fault message. A SOAP exception wraps the returned fault message.  
  
   If your orchestration does not return an error, use a different **Send** shape to send the standard SOAP response message using the usual response operation.  
  
## See Also  
 [Fault Messages](../core/fault-messages.md)   
 [Publishing an Orchestration as a Web Service](../core/publishing-an-orchestration-as-a-web-service.md)