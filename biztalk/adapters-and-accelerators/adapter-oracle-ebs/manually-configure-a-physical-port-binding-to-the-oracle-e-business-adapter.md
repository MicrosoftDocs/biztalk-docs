---
title: "Manually configure a physical port binding to the Oracle E-Business adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07369428-7b54-4d90-8c63-ba14e67fdbdd
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Manually configure a physical port binding to the Oracle E-Business adapter
This section provides information about configuring the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] as a WCF custom binding or as a WCF-OracleEBS port by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. After deploying the adapter, you will be able to send and receive messages from Oracle E-Business Suite by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. The steps for deploying the adapter vary depending on:  
  
- The direction of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. You may choose to configure a send, receive, send-receive, or a receive-send port. Your choices are summarized in the following table.  
  
  |Port direction|Communication pattern|Direction of communication to choose from|  
  |--------------------|---------------------------|-----------------------------------------------|  
  |Send|One-way|I will always be sending messages on this port.|  
  |Receive|One-way|I will always be receiving messages on this port.|  
  |Send-receive|Request-response|I will be sending a request and receiving a response.|  
  |Receive-send|Solicit-response|I will be receiving a request and sending a response.|  
  
   For more information, see the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Help documentation at [http://go.microsoft.com/fwlink/?LinkID=101130](http://go.microsoft.com/fwlink/?LinkID=101130).  
  
- Whether the adapter sends messages to or receives messages from Oracle E-Business Suite. Depending on whether you want to send or receive messages, you will create a send or receive port, respectively.  
  
  > [!NOTE]
  >  You can also configure the send or receive ports by importing a binding configuration file that is created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] as part of metadata generation. For instructions on configuring ports using this binding file, see [Configure a Physical Port Binding Using a Port Binding File to Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).  
  
## In This Section  
  
-   [Configuring a Port Using the WCF-Custom Adapter and Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-port-using-the-wcf-custom-adapter-and-oracle-e-business-suite.md)  
  
-   [Configuring a Port Using the WCF-OracleEBS Adapter](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-port-using-the-wcf-oracleebs-adapter.md)  
  
## See Also  
 [Building blocks to create Oracle E-Business Suite applications](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)