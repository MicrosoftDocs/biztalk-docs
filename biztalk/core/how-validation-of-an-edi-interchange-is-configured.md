---
title: "How Validation of an EDI Interchange Is Configured | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e698b21-e234-4d7d-b101-742eff68155c
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How Validation of an EDI Interchange Is Configured
If the process to look up an agreement determines the agreement to which an incoming or outgoing interchange resolves to, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the agreement properties (not pipeline properties) to determine how validation is performed. If no agreement resolves to an interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses some fallback agreement properties and some pipeline properties in performing validation.  
  
 The following tables indicate how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] determines the validations to perform on an EDI interchange. For the pipeline and fallback agreement columns in the table, "Yes" means that configuration is used if an agreement has not been determined.  
  
## General Information  
  
|Validation|Configured by Trading Partner|Configured by Pipeline<sup>*</sup>|Configured by Agreement|Configured by Fallback Agreement Settings|  
|----------------|-----------------------------------|----------------------------------------|-----------------------------|-----------------------------------------------|  
|Send port associations|Yes|No|Yes|No|  
|Certificates|Yes|No|No|No|  
|Status reporting|No|No|Yes|Yes|  
  
> [!NOTE]
>  Even though the settings are available through the pipeline, Microsoft recommends not setting the properties on the pipeline.  
  
## Agreement for outbound interchanges/BizTalk Receive Pipeline  
  
|Validation|Configured by Agreement|Configured by Pipeline<sup>*</sup>|Configured by Fallback Agreement Settings|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Business profile information: Contact and Contract Details|Yes|-|-|  
  
 **Validation of X12 Envelope Properties**  
  
|Validation|Configured by Agreement|Configured by Pipeline<sup>*</sup>|Configured by Fallback Agreement Settings|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Auth/Security|Yes|Available at agreement-level only|Available at agreement-level only|  
|Sender ID|Yes|Available at agreement-level only|Available at agreement-level only|  
|RepSeparator/<br />ISA11|Yes|Yes|No|  
|Duplicate/Validity at ISA|Yes|No|Yes|  
|Duplicate/Validity at GS|Yes|No|Yes|  
|Duplicate/Validity at ST|Yes|No|Yes|  
|NS/TS at Group Level|Yes|No|Yes|  
|Version/Release|Yes|Available at agreement-level only|Available at agreement-level only|  
  
 **Validation of EDIFACT Envelope Properties**  
  
|Validation|Configured by Agreement|Configured by Pipeline<sup>*</sup>|Configured by Fallback Agreement Settings|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Password|Yes|Available at agreement-level only|Available at agreement-level only|  
|SenderID|Yes|Available at agreement-level only|Available at agreement-level only|  
|NS/TS at Group level|Yes|No|Yes|  
|Version/Release|Yes|Available at agreement-level only|Available at agreement-level only|  
|Duplicate/Validity at UNB|Yes|No|Yes|  
|Duplicate/Validity at UNG|Yes|No|Yes|  
|Duplicate/Validity at UNH|Yes|No|Yes|  
|UNA Delimiters|No|Yes|No|  
  
 **General ACK Properties**  
  
|Validation|Configured by Agreement|Configured by Pipeline<sup>*</sup>|Configured by Fallback Agreement Settings|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|ACK on two way|Yes|Yes|No|  
|Generate functional ACK|Yes|No|Yes|  
|Batch interchange ACK|Yes|Available at agreement-level only|Available at agreement-level only|  
|Custom ACK control|Yes|No|Yes|  
|Generate interchange ACK|Yes|No|Yes|  
|Batch interchange ACK|Yes|Available at agreement-level only|Available at agreement-level only|  
|Custom ACK control|Yes|No|Yes|  
|Control reporting|Yes|No|Yes|  
  
 **Validation properties on payload**  
  
|Validation|Configured by Agreement|Configured by Pipeline<sup>*</sup>|Configured by Fallback Agreement Settings|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|EDI|Yes|Yes|No|  
|Extended|Yes|Yes|No|  
|Trailing separators|Yes|Yes|No|  
|Generate tags for trailing separators|Yes|Yes|No|  
|Masking security/password|Yes|Yes|No|  
|Decimal conversion|Yes|Yes|No|  
|Batching|-|-|-|  
|Preserve interchange|Yes|Yes|No|  
  
> [!NOTE]
>  Even though the settings are available through the pipeline, Microsoft recommends not setting the properties on the pipeline.  
  
## Agreement for inbound interchanges/BizTalk Send Pipeline  
 **X12 envelope generation**  
  
|Validation|Configured by Agreement|Configured by Pipeline<sup>*</sup>|Configured by Fallback Agreement Settings|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|ISA/GS/ST segments|Yes|No|Yes|  
  
 **EDIFACT envelope generation**  
  
|Validation|Configured by Agreement|Configured by Pipeline<sup>*</sup>|Configured by Fallback Agreement Settings|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|UNA/UNB/UNG/UNH segments|Yes|No|Yes|  
|UNA delimiters|Yes|No|Yes|  
  
 **Expected ACK Settings**  
  
|Validation|Configured by Agreement|Configured by Pipeline<sup>*</sup>|Configured by Fallback Agreement Settings|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Fn ACK setting|Yes|Available at agreement-level only|Available at agreement-level only|  
  
 **Validation properties on payload**  
  
|Validation|Configured by Agreement|Configured by Pipeline<sup>*</sup>|Configured by Fallback Agreement Settings|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|EDI|Yes|Yes|No|  
|Extended|Yes|Yes|No|  
|Trailing separators generation|Yes|Yes|No|  
  
 **Batch creation**  
  
|Validation|Configured by Agreement|Configured by Pipeline<sup>*</sup>|Configured by Fallback Agreement Settings|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Release criteria|Yes|Available at agreement-level only|Available at agreement-level only|  
|Range|Yes|Available at agreement-level only|Available at agreement-level only|  
|Filters|Yes|Available at agreement-level only|Available at agreement-level only|  
  
> [!NOTE]
>  Even though the settings are available through the pipeline, Microsoft recommends not setting the properties on the pipeline.  
  
## See Also  
 [EDI Message Validation](../core/edi-message-validation.md)