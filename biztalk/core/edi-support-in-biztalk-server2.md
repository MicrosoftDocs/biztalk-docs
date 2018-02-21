---
title: "EDI Support | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d4f50a9-fc55-400c-a63c-40b697425fea
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Support in BizTalk Server
EDI is built-in to BizTalk Server, and is an optional component when you install and configure BizTalk Server. 
  
## Feature Set Comparison Chart  
 The following table shows the EDI support included with BizTalk Server.
  
|Feature|Comment|  
|---|---|
|ISA    Segment modification at transaction set| Create TransactionSet-specific agreements|  
|ISA11:    US or other standard type| |  
|ISA12:    Interchange Control Version| |  
|ISA13:    Interchange Control Number (incrementing number)| |  
|ISA15:    Test or Production| |  
|GS    Segment modification at document/transaction level| |  
|GS    sender/receiver IDs allowed to be different than ISA| |  
|Inbound    Document IDs different than ISA & GS Outbound IDs| |  
|GS01:    Ability to change type of document| |  
|GS04:    Date (Ability to change format)|Contains UI to select format as CCYYMMDD and YYMMDD|  
|GS05:    Time (Ability to change format)|Contains UI to select format as HHMM, HHMMSS, and HHMMSSdd|  
|GS06:    Change the control number| |  
|GS07:    Agency Code| |  
|GS08:    Able to put in standards version| |  
|Ability to override EDI envelope at runtime| |  
|Custom    EDI Schemas| |  
|Organization/Party Setting|Create separate party and agreements. Also create agreements based off templates.|  
|EDI    document routing via document definition| |  
|Automatic 997’s to trading partners|Configuration specific to business profiles|  
|Outbound    EDI reliable messaging via 997’s| |  
|EDIFACT    Support|Supports D93 to D05 per ISO 9735 v4.1|  
|X12    Support|2040 to 5030|  
|HIPAA support| Microsoft BizTalk Accelerator for HIPAA (BTAHIPAA) as  part of native EDI functionality|  
|Ability to remove enumerators/codelists|Use Visual Studio/BizTalk Editor|  
|AS2    Send/Receive| AS2 is Drummond Certified for multi-file attachment support, file name preservation support and interoperability.|  
|AS2 file name preservation| |  
|AS2 reliable messaging| |  
|Outbound    Batching (accumulating multiple transaction types in a single transaction)|Supports multiple batch configurations for each business profile|  
|Inbound    Batching – Interchange XML (preserving an incoming ‘batched’ interchange) or Transaction Set XML based off configuration options|Also supports inbound-debatching, i.e., splitting interchange into individual Transaction Set Xml|  
|Interchange    and Transaction Set Generation and Validation in Design Time in Visual Studio| |  
|TA1    (Technical ACK) Generation and Reconciliation| |  
|Optional    EDI and XSD Validation flags| |  
|Document    format/definition at GS level| |  
  
## See Also  
 [EDI Standards Support](../core/edi-standards-support.md)   
 [EDI Document Schema Support](../core/edi-document-schema-support.md)   
 [EDI Character Set Support](../core/edi-character-set-support.md)