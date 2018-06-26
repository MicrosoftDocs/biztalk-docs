---
title: "Manually configure a physical port binding to the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, sending messages to the SAP system"
  - "physical port binding, manually configuring"
  - "deploying, receiving messages from the SAP system"
ms.assetid: c4f547aa-5514-4ca9-809b-d8d395de419c
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Manually configure a physical port binding to the SAP adapter
Configure the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] as a WCF custom binding by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. 

## Port overview
After deploying the adapter, you will be able to send and receive messages from the SAP system by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. The steps for deploying the adapter vary depending on:  
  
- The direction of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. You may choose to configure a Send, Receive, Send-Receive, or a Receive-Send port. Your choices are summarized in the following table:  
  
  |Port direction|Communication pattern|Direction of communication to choose from|  
  |---|---|---|  
  |Send|One-way|I will always be sending messages on this port.|  
  |Receive|One-way|I will always be receiving messages on this port.|  
  |Send-Receive|Request-response|I will be sending a request and receiving a response.|  
  |Receive-Send|Solicit-response|I will be receiving a request and sending a response.|  
  
   For more information, see [Create a Send Port](../../core/how-to-create-a-send-port2.md), or [Create a Receive Port](../../core/how-to-create-a-receive-port.md).
  
- Whether the adapter sends messages to the SAP system or receives messages from the SAP system. Depending on whether you want to send or receive messages, you will create a send or receive port.  
  
  > [!NOTE]
  >  You can also configure the send or receive ports by importing a binding configuration file that is created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] as part of metadata generation. For instructions on configuring ports using this binding file, see [Configure a physical port binding using a port binding file to SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).
  
## In this section  
  
-   [Configure a port using the WCF-custom adapter and Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/configure-a-port-using-the-wcf-custom-adapter-and-oracle-database-adapter.md)  
  
-   [Configure a port using the WCF-SAP adapter](../../adapters-and-accelerators/adapter-sap/configure-a-port-using-the-wcf-sap-adapter.md)  
  
## See Also  
[Building blocks to create SAP applications](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)