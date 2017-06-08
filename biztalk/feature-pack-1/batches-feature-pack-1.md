---
title: "Batches (Feature Pack 1) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: ed82bfdf-5d3b-4127-8d43-60520ee0cd66
caps.latest.revision: 6
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Batches (Feature Pack 1)
Managing Feature Pack 1 can be accomplished through a REST interface.

## Common tasks

[Batches](Batches.md)
- get  /Batches/{senderParty}/{receiverParty}/{agreementName} [Get batches from one party to another](../feature-pack-1/get-batches-from-one-party-to-another.md)
- post  /Batches/{senderParty}/{receiverParty}/{agreementName} [Create batch.](../feature-pack-1/create-batch.md)
- delete  /Batches/{senderParty}/{receiverParty}/{agreementName}/{batchName} [Delete batch.](../feature-pack-1/delete-batch.md)
- get  /Batches/{senderParty}/{receiverParty}/{agreementName}/{batchName} [Get a single batch from one party to another](../feature-pack-1/get-a-single-batch-from-one-party-to-another.md)
- put  /Batches/{senderParty}/{receiverParty}/{agreementName}/{batchName} [Update batch.](../feature-pack-1/update-batch.md)
- put  /Batches/{senderParty}/{receiverParty}/{agreementName}/{batchName}/{controlAction} [Send control message to batch.](../feature-pack-1/send-control-message-to-batch.md)
- get  /Batches/{senderParty}/{receiverParty}/{agreementName}/{batchName}/ActivationStatus [Get batch activation status](../feature-pack-1/get-batch-activation-status.md)
