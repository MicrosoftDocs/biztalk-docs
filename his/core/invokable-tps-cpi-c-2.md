---
description: "Learn more about: Invokable TPs (CPI-C)"
title: "Invokable TPs (CPI-C)"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invokable TPs (CPI-C)
An invokable transaction program (TP) is a TP that can be invoked by another TP. Invokable TPs are written or configured through registry or environment variables to supply their names to the SNA service as a notification that they are available for incoming requests. An SNA service invokable TP can be run on any computer running Host Integration Server or client.  
  
 There are two types of invokable TPs:  
  
 **Operator-started invokable TPs**  
 An operator-started invokable TP must be started by an operator before the TP can be invoked. When the operator-started invokable TP is started, it notifies the SNA service of its availability by issuing an [Accept_Conversation](./accept-conversation-cpi-c-2.md) call. The **Accept_Conversation** call causes the name of the invokable TP to be communicated to all the SNA services in the domain, along with the alias of an associated LU if one has been configured through a registry or environment variable.  
  
 **Autostarted invokable TPs**  
 An autostarted invokable TP can be started by the SNA service when needed. The TP must be registered through registry entries or environment variables on its local system, so that it can be identified to the SnaBase component of the SNA service. The registered information defines the TP as autostarted and must specify the TP name. The registered information can also specify the local LU alias that the invokable TP will use.  
  
 The recommended method for setting registry or environment variables for autostarted invokable TPs is to use the sample TP configuration program, TPSETUP, or similar code written into your own installation program. For more information about registry or environment variables for invokable TPs, see [Configuring Invokable TPs](../core/configuring-invokable-tps-cpi-c-1.md).  
  
 If no local LU alias is registered with autostarted TPs, the resulting SNA service configuration can be more flexible in responding to invoking requests. For more information about such flexible configurations, see [TP Name Not Unique; Local LU Alias Unspecified](../core/tp-name-not-unique;-local-lu-alias-unspecified-cpi-c-2.md).  
  
 After an autostarted invokable TP is started by SNA service, the TP issues [Accept_Conversation](./accept-conversation-cpi-c-2.md) just as an operator-started TP does. Accept_Conversation must provide the TP name that was registered for the TP.  
  
 Autostarted TPs must be configured through registry or environment variables to be either queued or nonqueued. All operator-started TPs act as queued TPs.  
  
 **Queued TPs**  
 If an autostarted TP is configured as queued, or if the TP is operator-started, incoming allocation requests are queued, and then sent only when the invokable TP issues **Accept_Conversation**. For autostarted invokable TPs, if a copy of the TP is not yet running, one is started when an incoming allocation request specifies that TP.  
  
> [!NOTE]
>  For the Microsoft Windows operating system, only one copy of a service can be running at any given time. This means that all autostarted TPs that run as services under Windows must be queued. To write an autostarted TP so it runs under Windows as a service and also runs in a nonqueued way, write a multithreaded program with an **Accept_Conversation** always outstanding.  
  
 **Nonqueued TPs**  
 If an autostarted TP is configured as nonqueued, a new copy will be started every time an [Allocate](./allocate-cpi-c-2.md) is received for the TP. Nonqueued TPs should process the conversation they have been allocated, and then exit, because they will not receive any additional **Allocate** requests.
