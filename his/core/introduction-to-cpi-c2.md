---
title: "Introduction to CPI-C2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97a24ed4-229b-4ed1-952e-cff9dc6df2d8
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Introduction to CPI-C
Common Programming Interface for Communications (CPI-C) is an application programming interface (API) that enables peer-to-peer communications among programs in a Systems Network Architecture (SNA) environment.  

 Through CPI-C, programs distributed across a network can work together, communicating with each other and exchanging data, to accomplish a single processing task such as querying a remote database, copying a remote file, or sending and receiving electronic mail.  

 The CPI-C calls and information presented in this section represent an evolving Microsoft® Windows® CPI-C that is composed of CPI-C version 1.2 and a set of Windows extensions that enable multiple applications and asynchronous call completion.  

 CPI-C version 1.0 was first introduced to provide a means by which two applications could speak and listen to each other; in other words, have a conversation. A conversation is the logical connection between two programs that enables the programs to communicate with each other. Programs using CPI-C converse with each other by making program calls. These calls are used to establish the full characteristics of the conversation, to exchange data, and to control the information flow between the two programs.  

 CPI-C version 1.1 includes four new areas of function:  

- Support for resource recovery (not supported in Windows CPI-C).  

- Automatic parameter conversion.  

- Support for communicating with non-CPI-C programs.  

- Local and remote transparency.  

  Built upon CPI-C version 1.1, X/Open CPI-C provided the following:  

- Support for nonblocking calls.  

- The ability to accept multiple conversations.  

- Support for data conversion (beyond parameters).  

- Support for security parameters.  

  CPI-C version 1.2 consolidated CPI-C version 1.1 and X/Open CPI-C and provided all the functions described previously. Windows CPI-C adds to this functionality by providing a set of extensions for asynchronous communication in addition to supporting most features in CPI-C version 1.2 with the exception of the following features:  

- Full duplex operation.  

- Nonblocking call behavior (as defined in the CPI-C 1.2 specification).  

- Some data conversion functions.  

  For a complete list of unsupported functions, see [CPI-C Functions Not Supported](./cpi-c-functions-not-supported-cpi-c-1.md).  

  The use of the CPI-C interface on Windows operating systems causes additional threads to be created within the calling process. These other threads perform interprocess communication with the SNA service over the local area network (LAN) interface that the client is configured to use (TCP/IP or named pipes, for example).  

  Stopping the SNABASE service causes the application to be unloaded from memory.  

  This section contains:  

- [Windows CPI-C Asynchronous Support](../core/windows-cpi-c-asynchronous-support1.md)  

- [Windows CPI-C Considerations](../core/windows-cpi-c-considerations1.md)  

- [Asynchronous Call Completion](../core/asynchronous-call-completion1.md)  

- [Initial Conversation Characteristics](../core/initial-conversation-characteristics1.md)  

- [Side Information for CPI-C Programs](../core/side-information-for-cpi-c-programs1.md)  

- [Configuration for CPI-C Programs](../core/configuration-for-cpi-c-programs1.md)  

- [CPI-C Considerations for Windows](../core/cpi-c-considerations-for-windows2.md)  

- [Finding Further Information about CPI-C](../core/finding-further-information-about-cpi-c2.md)
