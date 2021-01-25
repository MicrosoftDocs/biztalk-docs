---
description: "Learn more about: EDI Send Components"
title: "EDI Send Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fce270db-a573-48b3-be15-0178a5b7785b
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Send Components
The pipeline and pipeline components described in this topic process EDI messages that are not EDI/AS2 messages. For information about the sending of EDI/AS2 or non-EDI/AS2 messages, see [AS2 Send Components](../core/as2-send-components.md). Note that AS2 send components perform EDI processing in addition to AS2 processing.  
  
## EDI Send Pipeline  
 EDI send processing is performed in the following EDISend pipeline. This pipeline is installed in `Microsoft.BizTalk.Edi.EdiPipelines.dll` in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].  
  
 **EDISend Pipeline**  
  
 This pipeline generates and sends EDI messages. It does not process AS2-encoded EDI messages received over HTTP. Processing of AS2-encoded EDI messages is performed by an AS2 pipeline. The AS2 send pipelines use the same components to process EDI messages as the EDI pipeline uses.  
  
> [!NOTE]
>  Running the EDISend pipeline from an orchestration is not supported.  
  
> [!NOTE]
>  The AS2EDISend pipeline generates and sends EDI messages over AS2 transport. For more information, see [AS2 Send Components](../core/as2-send-components.md).  
  
 The pipeline consists of the EDI Assembler pipeline component:  
  
## EDI Send Pipeline Component  
 The EDISend pipeline uses the EDI Assembler pipeline component. This component is installed in `Microsoft.BizTalk.Edi.PipelineComponents.dll` in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Pipeline Components\\.  
  
 The EDI Assembler performs most processing of EDI-encoded interchanges in the EDISend Pipeline. For information about how the EDI Assembler processes EDI messages, see [How the EDI Assembler Works](../core/how-the-edi-assembler-works.md).
