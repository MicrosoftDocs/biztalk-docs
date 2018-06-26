---
title: "HIPAA Support in BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1ad8c64-6375-4364-80ce-440db943c222
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HIPAA Support in BizTalk Server
This topic provides a brief overview of HIPAA and how [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] supports HIPAA.  
  
## Introduction to HIPAA  
 The Health Insurance Portability and Accountability Act of 1996 (HIPAA) requires covered entities to use mandated standards when they electronically conduct transactions such as claims, remittance, eligibility, claims status requests and responses, and others. Covered entities under HIPAA are health plans, clearing houses, and most health care providers.  
  
## HIPAA support in BizTalk Server  
 Microsoft is committed to helping health care and allied organizations improve the way health care is delivered and financed. Microsoft intends to reduce the amount of time and money that organizations must spend complying with HIPAA regulations.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] helps organizations meet the challenges of creating automated business processes that connect and interoperate across diverse healthcare systems. Organizations affected by HIPAA can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]’s capabilities to help in developing, implementing, and integrating transaction-compliant solutions which also comply with federal law.  
  
[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] includes native functionality providing support for HIPAA. It is not an add-in to the product, such as an adapter or an accelerator. It is built into the product. [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] includes the EDI components and capabilities that are required to both comply with the HIPAA mandates and to also embrace HIPAA as a well-managed and measured business process.  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] supports HIPAA version 5010 and 4010.  
  
## HIPAA documentation in BizTalk Server  
 The primary EDI standards are X12 (standardized by ANSI and primarily used in North America) and EDIFACT (standardized by the United Nations and primarily used outside the U.S.). HIPAA is a standard derived from X12. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides HIPAA support as part of the native X12 EDI functionality. Therefore, where you see references to X12 support in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation, this support also applies to HIPAA processing, unless explicitly stated otherwise.  
  
 The following sections in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] have specific information about HIPAA.  
  
 **Getting Started**  
  
- [HIPAA Transaction Sets](../core/hipaa-transaction-sets.md)  
  
  **Planning and Architecture**  
  
- [HIPAA Document Schema Version 5010](../core/hipaa-document-schema-version-5010.md)  
  
- [HIPAA Schema Trigger Field Annotations](../core/hipaa-schema-trigger-field-annotations.md)  
  
- [Splitting HIPAA Subdocuments](../core/splitting-hipaa-subdocuments.md)  
  
  **Development**  
  
- [Modifying EDI Schemas](../core/modifying-edi-schemas.md) 

- [Customizing Enumerations in the Envelope Schema](../core/customizing-enumerations-in-the-envelope-schema.md)

- [Configuring Cross-Field Validation](../core/configuring-cross-field-validation.md)

  
 **Troubleshooting**  
  
-   [Known Issues with EDI Receive Processing](../core/known-issues-with-edi-receive-processing.md)  
  
-   [Known Issues with XML Tools Used with EDI Solutions](../core/known-issues-with-xml-tools-used-with-edi-solutions.md)  
  
## More information about HIPAA  
  
-   For information about the American National Standards Institute, Accredited Standards Committee for Electronic Data Interchange, go to [ASC X12 home](http://www.x12.org/).  
  
-   For information about X12's Insurance Subcommittee and their implementation guides adopted under HIPAA, go to [Washington Publishing Company's HIPAA EDI guides](http://www.wpc-edi.com/).
  
-   For information about the Workgroup for Electronic Data Interchange, go to [Workgroup for Electronic Data Interchange home page](http://www.wedi.org/).