---
title: "EDI Support in BizTalk Server2 | Microsoft Docs"
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
The different [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] versions support EDI through the following different features and components:  
  
|Release|Component/Feature Providing EDI Support|  
|---|---|  
|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)], and all newer versions|Native EDI functionality|  
|[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]|Base EDI Adapter|  
|[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)]|Base EDI Adapter|  
|[!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]|Native EDI functionality|  
  
## Feature Set Comparison Chart  
 The following table shows the EDI support provided by the EDI components/features in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] releases. ‘Y’ means the feature is supported; ‘N’ means the feature is not supported.  
  
|Feature|[!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] - [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]|[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] - [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]|BizTalk Server 2009|BizTalk Server 2010|Comment|  
|---|---|---|---|---|---|---|  
|ISA    Segment modification at transaction set|Y|N|Y|Y|Y|Supported in [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and later by creating TransactionSet-specific agreements.|  
|ISA11:    US or other standard type|Y|N|Y|Y|Y|-|  
|ISA12:    Interchange Control Version|Y|N|Y|Y|Y|-|  
|ISA13:    Interchange Control Number (incrementing number)|Y|N|Y|Y|Y|-|  
|ISA15:    Test or Production|Y|N|Y|Y|Y|-|  
|GS    Segment modification at document/transaction level|Y|N|Y|Y|Y|-|  
|GS    sender/receiver IDs allowed to be different than ISA|Y|N|Y|Y|Y|-|  
|Inbound    Document IDs different than ISA & GS Outbound IDs|Y|N|Y|Y|Y|-|  
|GS01:    Ability to change type of document|Y|N|Y|Y|Y|-|  
|GS04:    Date (Ability to change format)|N|N|Y|Y|Y|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and later contains UI to select format as CCYYMMDD and YYMMDD|  
|GS05:    Time (Ability to change format)|N|N|Y|Y|Y|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and later contains UI to select format as HHMM, HHMMSS, and HHMMSSdd|  
|GS06:    Change the control number|Y|N|Y|Y|Y|-|  
|GS07:    Agency Code|Y|N|Y|Y|Y|-|  
|GS08:    Able to put in standards version|Y|N|Y|Y|Y|-|  
|Ability to override EDI envelope at runtime|N|N|N|Y|Y|-|  
|Custom    EDI Schemas|Y|N|Y|Y|Y|-|  
|Organization/Party Setting|Y|Y (minimal)|Y|Y|Y|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and BizTalk Server 2009 enables you to create party based off templates.<br /><br /> BizTalk Server 2010 and later remodels this by separating party and agreements. Allows creating agreements based off templates.|  
|EDI    document routing via document definition|Y|-|Y|Y|Y|-|  
|Automatic    997’s to trading partners|Y|Y|Y|Y|Y|Supported in [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and BizTalk Server 2009 by party-specific configuration<br /><br /> Supported in BizTalk Server 2010 and later by configuration specific to business profiles.|  
|Outbound    EDI reliable messaging via 997’s|Y|Y|Y|Y|Y|-|  
|EDIFACT    Support|Y|Y (minimal)|Y|Y|Y|Supported in [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and later (D93 to D05 per ISO 9735 v4.1)|  
|X12    Support|Y|Y (minimal)|Y|Y|Y|Supported in [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and later (2040 to 5030)|  
|HIPAA support|N|Y (in [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)])|Y|Y|Y|Supported in [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] as Microsoft BizTalk Accelerator for HIPAA (BTAHIPAA) 3.3. Supported in [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and later as  part of native EDI functionality.|  
|Ability    to remove enumerators/codelists|Y|N|Y|Y|Y|Supported in [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and later by Visual Studio/BizTalk Editor|  
|AS2    Send/Receive|N|N|Y|Y|Y|In BizTalk Server 2009 and later, AS2 is Drummond Certified for multi-file attachment support, file name    preservation support and interoperability.|  
|AS2 file name preservation|N|N|N|Y|Y|-|  
|AS2 reliable messaging|N|N|N|Y|Y|-|  
|Can    migrate [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] custom XDR EDI schemas to EDI repository|-|N|N|N|N|You must migrate Base EDI applications to [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] or BizTalk Server 2009, and then use the Party Migration Tool to migrate the applications to BizTalk Server 2010 and later.|  
|Outbound    Batching (accumulating multiple transaction types in a single transaction)|N|N|Y|Y|Y|BizTalk Server 2009 and later supports multiple batch configurations for each business profile.|  
|Inbound    Batching – Interchange XML (preserving an incoming ‘batched’ interchange) or    Transaction Set XML based off configuration options|N|N|Y|Y|Y|In [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and later, this is in addition to supporting inbound-debatching, i.e., splitting interchange into individual Transaction Set Xml|  
|Interchange    and Transaction Set Generation and Validation in Design Time in Visual Studio|N|N|Y|Y|Y|-|  
|TA1    (Technical ACK) Generation and Reconciliation|N|N|Y|Y|Y|-|  
|Optional    EDI and XSD Validation flags|N|N|Y|Y|Y|-|  
|Document    format/definition at GS level|N|N|Y|Y|Y|-|  
  
## See Also  
 [EDI Standards Support](../core/edi-standards-support.md)   
 [EDI Document Schema Support](../core/edi-document-schema-support.md)   
 [EDI Character Set Support](../core/edi-character-set-support.md)