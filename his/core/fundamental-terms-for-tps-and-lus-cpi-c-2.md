---
description: "Learn more about: Fundamental Terms for TPs and LUs (CPI-C)"
title: "Fundamental Terms for TPs and LUs (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1da98197-7874-41d7-a2e0-0e4f61c4d6eb
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Fundamental Terms for TPs and LUs (CPI-C)
The following terms describe some fundamental characteristics of transaction programs (TPs) communicating through logical units (LUs):  
  
 *basic conversation*  
 A type of conversation more complex than a mapped conversation and generally used by service TPs (SNA-based programs that provide services to other programs). For a basic conversation, use [Set_Conversation_Type](./set-conversation-type-cpi-c-1.md) and specify CM_BASIC_CONVERSATION for the *conversation_type*. For more information, see [Basic and Mapped Conversations Compared](../core/basic-and-mapped-conversations-compared-cpi-c-2.md).  
  
 *conversation*  
 The interaction between TPs carrying out a specific task. Each conversation requires an LU-LU session. A TP can be involved in several conversations simultaneously, as shown with TP B in [Communication Between TPs](../core/communication-between-tps-cpi-c-2.md).  
  
 *invokable TP*  
 A TP that can be invoked by another TP. Invokable TPs are usually server-type applications. That is, they work in the same general way that an IBM CICS application works. Parameters for an invokable TP are configured through registry or environment variables.  
  
 There are several types of invokable TPs:  
  
 *operator-started invokable TP*  
  
 A TP that is started manually in preparation for being invoked.  
  
 *autostarted invokable TP*  
  
 A TP that is automatically started by Common Programming Interface for Communications (CPI-C) when invoked.  
  
 *queued TP*  
  
 A TP that, when invoked multiple times, loads once, and then queues up subsequent requests to be dealt with one at a time. All operator-started TPs and some autostarted TPs are queued.  
  
 *nonqueued TP*  
  
 A TP loaded multiple times, once for every time it is invoked. Some autostarted TPs are nonqueued but no operator-started TPs are nonqueued.  
  
 For more information, see [Invokable TPs](../core/invokable-tps-cpi-c-2.md).  
  
 *invoking TP*  
 A TP that can invoke (that is, initiate a conversation with) other TPs. Invoking TPs are usually client-type applications. That is, they work in the same general way that an emulator works. For more information see [Invoking TPs](../core/invoking-tps-cpi-c-2.md).  
  
 *local LU and local TP*  
 An LU and TP working together, when viewed as the home base for a particular conversation. From this viewpoint, some other LU and TP are seen as the partner or remote LU and TP.  
  
 *LU alias*  
 The string that identifies an LU to a TP. The alias can be up to eight characters long.  
  
 *LU-LU session*  
 The communication between two LUs over a specific connection for a specific amount of time. An LU-LU session is needed for two TPs to interact. One session can be used serially by many pairs of TPs.  
  
 An LU 6.2 can have multiple sessions (two or more concurrent sessions with different partner LUs) and parallel sessions (two or more concurrent sessions with the same partner LU).  
  
 LUs are configured through SNA Manager on Host Integration Server. This administration tool is also used to configure LU-LU pairs and modes. The LU and mode configurations control how many sessions a particular LU-LU pair supports.  
  
 *mapped conversation*  
 A type of conversation simpler than a basic conversation and generally used by application TPs (programs that accomplish tasks for end users). The default for conversation type is mapped. The conversation type can be changed with the [Set_Conversation_Type](./set-conversation-type-cpi-c-1.md) call. For more information, see [Basic and Mapped Conversations Compared](../core/basic-and-mapped-conversations-compared-cpi-c-2.md).  
  
 *partner LU and partner TP, or remote LU and remote TP*  
 An LU and TP working together, when viewed as being at the far end of a particular conversation.
