---
title: "HL7 2.4 XML Folders and Events | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "events, HL7 2.XML versions"
  - "HL7, default sub-folders"
  - "HL7, events"
ms.assetid: bc6c5d75-66c7-4269-bfb9-59cab5999a73
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HL7 2.4 XML Folders and Events
The following table lists the subfolders created by the setup wizard within the HL7 version 2.4 folder for XML-encoded messages. These subfolders contain the schemas used by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table. The subfolder names describe the types of events these schemas support.  
  
|Sub folder|Events|  
|----------------|------------|  
|Patient Administration|A01-A62, K21,K22,K23,K24,Q21-Q24|  
|Order Entry|O01-O22, Q06, Q26-Q30, RAR,RDR,RER,RGR,ROR, V01-V04, Z73, Z74|  
|Query|J01,J02,K11,K13,K15, Q01-Q05, Q07-Q09, Q11,Q13,Q15-Q17, R07-R09, Z75-Z99|  
|Financial Management|P01~P06, P10|  
|Observation Reporting|C01-C12, P07,P08,P09, R01,R02,R04, R21, W01, W02|  
|Master Files|M01-M12, MFA|  
|Medical Records/Information Management|T01-T12|  
|Scheduling|S01-S26|  
|Patient Referral|I01-I15|  
|Patient Care|PC1-PCH, PCJ,PCK,PCL|  
|Clinical Laboratory Automation|U01-U13|  
|Application Management|N01,N02|  
|Personnel Management|B01-B06, K25,Q25|  
  
## See Also  
 [Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)