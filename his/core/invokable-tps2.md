---
title: "Invokable TPs | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8e063a8f-d0ff-4958-bc60-273bc1bd9e06
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Invokable TPs
An invokable TP is a TP that can be invoked by another TP. Invokable TPs are written or configured through registry or environment variables to supply their names to Host Integration Server as a notification that they are available for incoming requests. Invokable TPs can be run on any Host Integration Server client or server running Windows.  
  
 There are two types of invokable TPs:  
  
 **Operator-started invokable TPs**  
 An operator-started invokable TP must be started by an operator before the TP can be invoked. When the operator-started invokable TP is started, it notifies Host Integration Server of its availability by issuing a [RECEIVE_ALLOCATE](./receive-allocate1.md) verb. The **RECEIVE_ALLOCATE** causes the name of the invokable TP, along with the alias of an associated LU if one has been configured through a registry or environment variable, to be communicated to all the servers running Host Integration Server in the SNA domain.  
  
 **Autostarted invokable TPs**  
 An autostarted invokable TP can be started by Host Integration Server when needed. The TP must be registered through registry entries or environment variables on its local system, so that it can be identified to the SnaBase component of the Host Integration Server client software. The registered information defines the TP as autostarted and must specify the TP name. The registered information can also specify the local LU alias that the invokable TP will use.  
  
 The recommended method for setting registry or environment variables for autostarted invokable TPs is to use the sample TP configuration program, TPSETUP, or similar code written into your own installation program. For more information about registry or environment variables for invokable TPs, see [Configuring Invokable TPs](../core/configuring-invokable-tps1.md). 
  
 If no local LU alias is registered with autostarted TPs, the resulting Host Integration Server configuration can be more flexible in responding to invoking requests. For more information about such flexible configurations, see [TP Name Not Unique; Local LU Alias Unspecified](../core/tp-name-not-unique;-local-lu-alias-unspecified-sna-2.md).  
  
 After an autostarted invokable TP is started by Host Integration Server, the TP issues [RECEIVE_ALLOCATE](./receive-allocate1.md) just as an operator-started TP does. **RECEIVE_ALLOCATE** must provide the TP name that was registered for the TP.  
  
 Autostarted TPs must be configured through registry or environment variables to be either queued or nonqueued. All operator-started TPs act as queued TPs.  
  
 **Queued TPs**  
 If an autostarted TP is configured as queued, or if the TP is operator-started, incoming allocation requests are queued and then sent only when the invokable TP issues **RECEIVE_ALLOCATE**. For autostarted invokable TPs, if a copy of the TP is not yet running, one is started when an incoming allocation request specifies that TP.  
  
> [!NOTE]
>  For Windows, only one copy of a service can be running at any given time; this means that all autostarted TPs that run as services under Windows must be queued. To write an autostarted TP so it will run under Windows as a service and also run in a nonqueued way, write a multithreaded program with a **RECEIVE_ALLOCATE** always outstanding.  
  
 **Nonqueued TPs**  
 If an autostarted TP is configured as nonqueued, a new copy will be started every time an [ALLOCATE](./allocate2.md) or [MC_ALLOCATE](./mc-allocate2.md) is received for the TP. Nonqueued TPs should process the conversation they have been allocated and then exit, since they will not receive any additional **ALLOCATE** or **MC_ALLOCATE** requests.