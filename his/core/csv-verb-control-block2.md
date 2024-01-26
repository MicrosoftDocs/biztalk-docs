---
description: "Learn more about: CSV Verb Control Block"
title: "CSV Verb Control Block2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# CSV Verb Control Block
The only parameter passed to the **WINCSV** function is the address of a verb control block (VCB). The VCB is a structure made up of variables that identify the verb to be executed, supply information to be used by the verb, and contain information returned by the verb when execution is complete. Each verb has its own VCB structure, which is declared in the file WINCSV.H.
