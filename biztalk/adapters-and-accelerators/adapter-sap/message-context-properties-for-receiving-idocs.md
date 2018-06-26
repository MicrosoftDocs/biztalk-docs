---
title: "Message Context Properties for Receiving IDOCs | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDOCs, message context properties for receiving"
ms.assetid: fadb2284-2f55-49c2-bae9-95325f1be539
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Context Properties for Receiving IDOCs
For receiving an IDOC using Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the following message context properties.  
  
 **IDOC Control Record properties.**  
  
- **TABNAM** - Name of table structure  
  
- **MANDT** - Client  
  
- **DOCNUM** - IDOC number  
  
- **DOCREL** - SAP Release for IDOC  
  
- **STATUS** - Status of IDOC  
  
- **DIRECT** - Direction  
  
- **OUTMOD** - Output mode  
  
- **EXPRSS** - Overriding in inbound processing  
  
- **TEST** - Test flag  
  
- **IDOCTYP** - Name of basic type  
  
- **CIMTYP** - Extension (defined by customer)  
  
- **MESTYP** - Message type  
  
- **MESCOD** - Message code  
  
- **MESFCT** - Message function  
  
- **STD** - EDI standard, flag  
  
- **STDVRS** - EDI standard, version and release  
  
- **STDMES** - EDI message type  
  
- **SNDPOR** - Sender port (SAP System, external subsystem)  
  
- **SNDPRT** - Partner type of sender  
  
- **SNDPFC** - Partner Function of Sender  
  
- **SNDPRN** - Partner Number of Sender  
  
- **SNDSAD** - Sender address (SADR)  
  
- **SNDLAD** - Logical address of sender  
  
- **RCVPOR** - Receiver port  
  
- **RCVPRT** - Partner Type of receiver  
  
- **RCVPFC** - Partner function of recipient  
  
- **RCVPRN** - Partner number of recipient  
  
- **RCVSAD** - Recipient address (SADR)  
  
- **RCVLAD** - Logical address of recipient  
  
- **CREDAT** - Created on  
  
- **CRETIM** - Time Created  
  
- **REFINT** - Transmission file (EDI Interchange)  
  
- **REFGRP** - Message group (EDI Message Group)  
  
- **REFMES** - Message (EDI Message)  
  
- **ARCKEY** - Key for external message archive  
  
- **SERIAL** - Serialization  
  
- **DOCTYP** - IDOC type (This is available in EDI_DC only. Should be present in the context property but should be promoted for Version 2 IDOCs only)  
  
  **TID** – Represents the TID sent by the SAP system for the incoming TRFC call.  
  
  **GUID** – Represents the GUID which the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses internally. This has a one-to-one mapping with the TID which was received from the SAP system.  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)