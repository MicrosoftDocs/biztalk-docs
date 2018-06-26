---
title: "Manually configure a physical port binding to the Oracle Database Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, sending to an Oracle database"
  - "messages, receiving from an Oracle database"
  - "physical port binding, manually configuring"
ms.assetid: 6b118236-e9eb-494e-96b2-969c7064943d
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Manually configure a physical port binding to the Oracle Database Adapter
This section provides information about configuring the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] as a WCF-Custom binding or WCF-OracleDB binding by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. After deploying the adapter, you will be able to send and receive messages from the Oracle database by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. The steps for deploying the adapter vary depending on:  
  
- The direction of communication between BizTalk Server and [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. You may choose to configure a send, receive, send-receive, or a receive-send port. Your choices are summarized in the following table.  
  
  |Port direction|Communication pattern|Direction of communication to choose from|  
  |--------------------|---------------------------|-----------------------------------------------|  
  |Send|One-way|I will always be sending messages on this port.|  
  |Receive|One-way|I will always be receiving messages on this port.|  
  |Send-receive|Request-response|I will be sending a request and receiving a response.|  
  |Receive-send|Solicit-response|I will be receiving a request and sending a response.|  
  
   For more information, see [Create a Send Port](../../core/how-to-create-a-send-port2.md), or [Create a Receive Port](../../core/how-to-create-a-receive-port.md). 
  
- Whether the adapter sends messages to the Oracle database or receives messages from the Oracle database. Depending on whether you want to send or receive messages, you will create a send or receive port, respectively.  
  
  > [!NOTE]
  >  You can also configure the send or receive ports by importing a binding configuration file that is created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] as part of metadata generation. For instructions on configuring ports using this binding file, see [Configure a physical port binding using a port binding file to Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).  
  
 
  
## See Also  
[Develop your BizTalk applications](../../core/develop-your-biztalk-applications.md)