---
title: "HIPAA Document Schema Version 5010 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62e50964-66e1-4ed9-a1a1-68556b13b024
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HIPAA Document Schema Version 5010
The U.S. Department of Health and Human Services (HHS) announced a final rule on January 16, 2009, that replaces the current HIPAA version 4010A1 with version 5010. Version 5010 of the HIPAA standards includes improvements in structural, front matter, technical, and data content. These improvements will reduce and eliminate ambiguities in data while also addressing a few previously unmet business needs. BizTalk Server provides support for HIPAA version 5010.  

> [!NOTE]
>  BizTalk Server continues to support HIPAA version 4010A1.  

## HIPAA 5010 Version Support  
 The following changes have been introduced as part of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]’s support for HIPAA 5010:  

- **New replacement schemas**: HIPAA version 5010 introduces the following new replacement schemas over the earlier version 4010A1. EDI schemas are compressed and delivered in the executable, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\MicrosoftEdiXSDTemplates.exe. When executed, MicrosoftEdiXSDTemplates.exe deposits HIPAA 5010 schemas into [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\HIPAA\5010 folder.  


  |  GS08/ST03   | Set IDs (ST01) |                       Description                       |
  |--------------|----------------|---------------------------------------------------------|
  |  005010X279  |      270       |   Eligibility, Coverage or Benefit Inquiry - Request    |
  |  005010X279  |      271       | Eligibility, Coverage or Benefit Information - Response |
  |  005010X212  |      276       |           Health Care Claim Status - Request            |
  |  005010X212  |      277       |           Health Care Claim Status - Response           |
  |  005010X217  |      278       |   Health Care Services Review – Request and Response    |
  |  005010X218  |      820       |                    Payroll Deduction                    |
  |  005010X220  |      834       |    Health Care Benefit(s) Enrollment and Maintenance    |
  |  005010X221  |      835       |              Health Care Claim Payment(s)               |
  |  005010X222  |      837       |           Health Care Claim(s) - Professional           |
  | 005010X223A1 |      837       |          Health Care Claim(s) - Institutional           |
  | 005010X224A1 |      837       |              Health Care Claim(s) - Dental              |


- **Support for ST03 field**: Version 5010 mandates the presence of ST03 in all transaction sets other than 835 (Health Care Claim Payment(s)). ST03 is used to identify the version of the transaction set. ST03 allows different versions of transaction sets within a single group. ST03 precedes over GS08 in identifying the transaction set version. You can write and promote ST03 under the EDI property schema namespace as a context property and route messages based on ST03.  

- **Support for similar transaction sets within a group**: X12 standards provide a mapping between transaction sets and groups, known as the ST01-GS01 mapping. This mapping is used to validate similar transaction sets which can be combined within a single group (GS-GE). For HIPAA, this implies that a Professional, Institutional and Dental 837 claim can now occur within a single group.  

- **Support for ICD-10**: Electronic transaction code sets are used for the transmission of healthcare data. Version 5010 accommodates the use of the International Classification of Diseases (ICD-10) code sets, which are not supported by earlier version 4010A1. ICD-10 is used for identifying various diagnoses and procedures in claim billing, related transactions and clinical reporting. The benefits of using ICD-10 include more accurate data on patient services, diagnosis, treatment information and more comprehensive reporting of quality data.  

- **New fields in 5010 997**: The 997 functional acknowledgement schema provided out-of-the-box by BizTalk Server introduces three new optional fields namely AK103, AK203 and AK41.3. The EDI engine is capable of processing an incoming 5010 997 message which contains these fields but will not generate an outgoing 997 acknowledgement based on the new schema.  

  There was a known issue with the HIPAA 4010A1 schemas in which elements of the X12_R data type were not checked against their minimum and maximum lengths. In BizTalk Server this issue has been fixed and the HIPAA 5010 schemas validate elements of the X12_R data type for the minimum and maximum lengths.  

## See Also  
 [HIPAA Support in BizTalk Server](../core/hipaa-support-in-biztalk-server.md)   
 [Splitting HIPAA Subdocuments](../core/splitting-hipaa-subdocuments.md)