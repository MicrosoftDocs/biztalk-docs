---
title: "Sample Business Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BTAHL7, business example"
  - "examples, business processes"
  - "health care organizations, business example"
  - "business processes, example"
ms.assetid: 54bfbe45-4638-4488-bbd8-c642926a35d3
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sample Business Scenario
Health care processes are often complex and involve many systems. An example is the process that occurs when a patient enters a hospital, and a physician sends the patient for a lab test. Involved in this procedure are five parties:  
  
- The attending physician  
  
- The Hospital Registration System  
  
- The Clinical Order Entry System  
  
- The Laboratory System  
  
- The Billing System  
  
  The following steps might occur in this process:  
  
1.  The attending doctor registers the patient.  
  
    1.  An ADT^O04 registration message is broadcast by the Hospital Registration System.  
  
    2.  The ADT^O04 message is received by all departments that subscribe to the message, including the Clinical Order Entry System and the Laboratory System.  
  
2.  The doctor orders a diagnostic study from the laboratory facility.  
  
    1.  An ORM^O01 order message is sent from the Clinical Order Entry System, after validation of business rules.  
  
    2.  The ORM^O01 message is received by the Laboratory System.  
  
3.  The laboratory receives the order, and returns a confirmation.  
  
    1.  An ORR^O02 order-confirmation message is sent by the Laboratory System, indicating that the order can be executed.  
  
    2.  The ORR^O02 message is received by the Clinical Order Entry System.  
  
4.  On completion of the tests, the laboratory sends the results to the doctor and other departments.  
  
    1.  An ORU^R01 test-results message is sent from the Laboratory System.  
  
    2.  The ORU^R01 message is received by the Clinical Order Entry System and the Billing System.  
  
    3.  The Interface Engine sends out an e-mail message to the doctor, who receives the lab results on his wireless PDA.  
  
## The BTAHL7 Solution  
 The sample business scenario outlined above is an example of a health care system that needs integration. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) provides a solution for this scenario that features the following functionality:  
  
1. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] integrates all of the systems involved in a hub-and-spoke arrangement. Each system communicates directly with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. They do not have to communicate directly to each other.  
  
2. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] handles HL7-encoded messages natively. No custom coding is required.  
  
3. The ADT^O04 registration message is broadcast to all systems that subscribe to it. The publisher-subscriber messaging model for [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] provides flexibility in setting up and maintaining the list of systems subscribing to the message. You can add systems to or delete them from the subscription list without affecting the rest of the system.  
  
4. The business rule used to validate the ORM^O01 order message can be changed dynamically without affecting the rest of the system.  
  
5. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] can be configured to automatically generate the ORR^O02 order-confirmation (ACK) message.  
  
6. If necessary, you can batch any of the messages with others for sending, and process them on receipt from within the batch.  
  
7. You can validate all messages in the engine and against the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2X schemas published by the HL7 organization.  
  
## See Also  
 [How BizTalk Server Solves the Business Need](../../adapters-and-accelerators/accelerator-hl7/how-biztalk-server-solves-the-business-need2.md)