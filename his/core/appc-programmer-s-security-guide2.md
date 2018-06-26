---
title: "APPC Programmer&#39;s Security Guide2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9ff7d5f5-2198-440d-8e6b-8814f2ec5575
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# APPC Programmer&#39;s Security Guide
The following topics discuss security as it applies to the APPC section of the Microsoft Host Integration Server SDK.  
  
## About APPC security for developers  
 This section discusses security practices and issues that apply to C-language applications that you write to use Advanced Program-to-Program Communications (APPC) to exchange data in a Systems Network Architecture (SNA) environment.  
  
### Conversation Security  
  
- Owners of APPC transaction programs may want to allow only a limited set of users to start the program. APPC provides a mechanism, called APPC conversation security, where the client transaction program supplies credentials to the server to gain access to the program. You can find more information on conversation security in the section: APPC Security.  
  
  Several APPC verbs create a connection with a remote LU. When creating a connection with a remote LU, credentials may be required to establish access. The **security** parameter controls conversation security, and the **pwd** and **user_id** parameters specify the information used to validate the user on the host.  
  
  Conversational security is documented in the topic [Conversation Security](../core/conversation-security2.md), and in the reference pages for the following APPC verbs:  
  
- [ALLOCATE](./allocate2.md)  
  
- [MC_ALLOCATE](./mc-allocate2.md)  
  
- [SEND_CONVERSATION](./send-conversation2.md)  
  
- [MC_SEND_CONVERSATION](./mc-send-conversation1.md)  
  
### Session Security configuration using SNACFG  
 You can use the utility SNACFG to set session security for a remote LU. Possible values are none, use a plaintext key, and use a scrambled key.  
  
### Automatic Login  
 The configuration of Host Integration Server to support automatic login is discussed in the topic [Support for CPI-C Automatic Logon](../core/support-for-cpi-c-automatic-logon1.md).  
  
### Setting the service key with CNOS  
 You can specify a master or service key using the **key** parameter when changing the number of sessions with the [CNOS](./cnos2.md) verb. This is a plaintext parameter, and is valid if the keylock feature has been secured.