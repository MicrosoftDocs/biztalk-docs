---
description: "Learn more about: CSV Verb Control Block"
title: "CSV Verb Control Block2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7463292c-1751-4008-9e9e-729175ae317f
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# CSV Verb Control Block
The only parameter passed to the **WINCSV** function is the address of a verb control block (VCB). The VCB is a structure made up of variables that identify the verb to be executed, supply information to be used by the verb, and contain information returned by the verb when execution is complete. Each verb has its own VCB structure, which is declared in the file WINCSV.H.
