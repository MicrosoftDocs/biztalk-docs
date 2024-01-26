---
description: "Learn more about: Verb Control Block"
title: "Verb Control Block2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Verb Control Block
The only parameter passed to the **APPC** function is the address of a verb control block (VCB). The VCB is a structure made up of variables that:  
  
- Identify the APPC verb to be executed.  
  
- Supply information to be used by the verb.  
  
- Contain information returned by the verb when execution is complete.  
  
  Each APPC verb has its own VCB structure, which is declared in the WINAPPC.H header file. For compatibility with earlier versions, the APPC_C.H header file is also supported.  
  
  The WINAPPC.H file is supplied as part of the Host Integration Server Software Development Kit (SDK).
