---
title: "Logging Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring, auditing"
  - "configuring, logging"
  - "logging, configuring"
  - "auditing, configuring"
ms.assetid: 5cd7aec1-bd38-4d37-9a79-b01eeb89337d
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Logging Configuration
Together, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server and [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] offer secure transactional and digital Enterprise Application Integration (EAI) communications for health care providers such as hospitals, clinics, and nursing homes. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] provides the ability to coordinate application activity and transaction processing, dynamically route messages, validate and transform data, and transport over a variety of adapters. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] supports the American National Standards Institute (ANSI)-accredited Health Level Seven (HL7) messaging standard used by clinical and administrative applications in provider networks to exchange medical data in real-time.  
  
 The HL7 messages that pass through the accelerator system can be very critical. For example, the data could be a patient's medical record or a financial transaction. To ensure compliance with HL7 security and privacy regulations, system administrators must be able to do the following:  
  
- Debug suspended messages  
  
- Monitor system and file access on an ongoing basis to detect potential intruders and reduce the risk of security breaches  
  
  This section provides conceptual and procedural information to enable you to configure auditing and logging, examine and interpret audit data and event logs, and run queries against the logged data.  
  
## In This Section  
  
-   [About the Logging Process](../../adapters-and-accelerators/accelerator-hl7/about-the-logging-process.md)  
  
-   [Configuring Logging](../../adapters-and-accelerators/accelerator-hl7/configuring-logging.md)