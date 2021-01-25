---
description: "Learn more about: APPC Verb Overview"
title: "APPC Verb Overview2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 74b11ee8-0e66-412d-92c6-5f7585d5bfef
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# APPC Verb Overview
APPC verbs fall into three categories: management, transaction program (TP), and conversation.  
  
## Management Verbs  
 Management verbs provide management functions. They are:  
  
 ACTIVATE_SESSION  
  
 CNOS  
  
 DEACTIVATE_SESSION  
  
 DISPLAY  
  
## TP Verbs  
 TP verbs start and end TPs, and get and set TP properties. They are:  
  
 GET_TP_PROPERTIES  
  
 SET_TP_PROPERTIES  
  
 TP_ENDED  
  
 TP_STARTED  
  
## Conversation Verbs  
 Conversation verbs enable TPs to allocate and deallocate conversations, send and receive data, and change conversation states. The conversation verbs are listed in the following table.  
  
 Conversation verbs fall into two groups: mapped conversation verbs and basic conversation verbs. The mapped conversation is intended for programs that use the conversation directly. The basic conversation is intended for more complex programs that provide services to other users. In typical situations, end-user TPs use mapped conversations and service TPs use basic conversations.  
  
 Mapped conversation verbs can only be issued by a TP in mapped conversations, while basic conversation verbs are reserved for basic conversations. There is one exception to this rule: ALLOCATE can be used to start either a basic or a mapped conversation.  
  
|Mapped conversation verbs|Basic conversation verbs|  
|-------------------------------|------------------------------|  
|MC_ALLOCATE|ALLOCATE|  
|MC_CONFIRM|CONFIRM|  
|MC_CONFIRMED|CONFIRMED|  
|MC_DEALLOCATE|DEALLOCATE|  
|MC_FLUSH|FLUSH|  
|MC_GET_ATTRIBUTES|GET_ATTRIBUTES|  
|GET_LU_STATUS|GET_LU_STATUS|  
|GET_STATE|GET_STATE|  
|GET_TYPE|GET_TYPE|  
|MC_POST_ON_RECEIPT|POST_ON_RECEIPT|  
|MC_PREPARE_TO_RECEIVE|PREPARE_TO_RECEIVE|  
|RECEIVE_ALLOCATE|RECEIVE_ALLOCATE|  
|MC_RECEIVE_AND_POST|RECEIVE_AND_POST|  
|MC_RECEIVE_AND_WAIT|RECEIVE_AND_WAIT|  
|MC_RECEIVE_IMMEDIATE|RECEIVE_IMMEDIATE|  
|MC_RECEIVE_LOG_DATA|RECEIVE_LOG_DATA|  
|MC_REQUEST_TO_SEND|REQUEST_TO_SEND|  
|MC_SEND_CONVERSATION|SEND_CONVERSATION|  
|MC_SEND_DATA|SEND_DATA|  
|MC_SEND_ERROR|SEND_ERROR|  
|MC_TEST_RTS|TEST_RTS|  
  
 Mapped and basic verbs have the same functions in their respective types of conversation. For example, **MC_CONFIRM** performs the same function in a mapped conversation that **CONFIRM** performs in a basic conversation.
