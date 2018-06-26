---
title: "FIN Response Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, response types"
  - "deploying, schemas"
  - "FIN Response Reconciliation, message types"
  - "FRR, deploying schemas"
  - "schemas, deploying"
  - "FIN Response Reconciliation, response types"
  - "messages, message types"
  - "response types [FIN Response Reconciliation]"
ms.assetid: a6ef2f20-08ab-40d3-a0a5-cc4048ce0987
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FIN Response Types
FIN Response Reconciliation (FRR) reconciles responses to any Category 0 to 9 SWIFT FIN message. In response to one of these FIN messages, the SWIFT FIN application always sends at least one, and possibly more than one, acknowledgment (ACK) or negative acknowledgment (NAK). The following table shows the message types of the outbound and inbound (response) messages processed by FRR.  


| Outbound/<br /><br /> inbound |                                             Message type                                              |                                                                                                                                                                                                                             Message status                                                                                                                                                                                                                              |
|-------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Outbound            |                              All Category 0 to 9 SWIFT FIN message types                              |                                                                                                                                                                                                                                   N/A                                                                                                                                                                                                                                   |
|            Inbound            |                         MQ Series PAN/NAN (MQ Series transport-level ACK/NAK)                         |                                                                                                                                                                                                                    MQSeries transport acknowledgment                                                                                                                                                                                                                    |
|                               |                                     MT010 (Non-Delivery Warning)                                      |                                                                     SWIFT successfully sent the original message to the partner, but has no indication that the partner received the message. If [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receives multiple Non-Delivery Warning (NDW) messages, it loops and waits for the next expected message.                                                                     |
|                               |                                     MT011 (Delivery Notification)                                     |                                                                                                                                                                     SWIFT successfully sent the original message to the partner, and received an indication that the partner received the message.                                                                                                                                                                      |
|                               |                                      MT012 (Sender Notification)                                      |                                                                                                                                                            SWIFT successfully received the original message from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].                                                                                                                                                             |
|                               |                                      MT015 (DNK, or Delayed NAK)                                      |                                                                                                                                                                                                  SWIFT has not successfully sent the original message to the partner.                                                                                                                                                                                                   |
|                               |                                      MT019 (Abort Notification)                                       |                                                                                                                                                                                                                 Message transmission aborted at SWIFT.                                                                                                                                                                                                                  |
|                               | MTS21_FIN_ACKNAK (Acknowledgment or negative acknowledgment of a FIN message sent by an LT (ACK/NAK)) | SWIFT successfully or unsuccessfully received the message from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. This message covers both of these cases. Whether it is an ACK or a NAK is determined by the value in the 451 field of the message ("0" for ACK and "1" for NAK). This will be the first response delivered back to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. |

## Deployment of Schemas for FRR  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] setup deploys schemas in FrrSchemas.dll for all system-level messages (as shown in the table above). The FRR orchestration requires these schemas to be deployed. Because [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] setup deploys these schemas in FrrSchemas.dll, you do not have to, and must not, deploy these schemas in another project. Doing so will generate an error.  

 FRRSchemas.dll includes the following schemas:  

-   TransportAck  

-   MT010  

-   MT011  

-   MT012  

-   MT015  

-   MT019  

-   MTS21_FIN_ACKNAK