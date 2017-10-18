---
title: "Adapters and Accelerators in BizTalk Server | Microsoft Docs"
description: Overview of all the adapters and accelerators in BizTalk, including the built-in adapters, BAP, HL7, Swift, RosettaNet, FileAct, and InterAct
caps.latest.revision: 3
author: "MandiOhlinger"
manager: "anneta"

ms.custom: ""
ms.date: "08/09/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df7f26a1-e47b-4323-b9f0-58842c55a6f8
ms.author: "mandia"

---
# Adapters and Accelerators in BizTalk Server
 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] includes different adapters and accelerators for you to create applications that receive data, and send data to different services and LOB systems. 
 
This section describes the different adapters and accelerators available with  [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. 

## Out-of-the-box adapters
When you install BizTalk Server, you also install the built-in adapters that are ready to be used. Some of these adapters include File, FTP, MQ Series, Service Bus, Logic Apps, POP3, SharePoint, and more.

**[Using Adapters](../core/using-adapters.md) lists all of them, and also shows you how to use each adapter.**
 
## BizTalk Adapter Pack
The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] is included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and provides WCF-based adapters to connect your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to Oracle, SAP, Siebel, and SQL Server. You can also create your own WCF-based adapters using the [!INCLUDE[afproductnameshort_md](../includes/afproductnameshort-md.md)]. 

**See [BizTalk Adapter Pack](../adapters-and-accelerators/biztalk-adapter-pack.md) to install and configure these adapters, step through tutorials and scenarios, create applications using the different adapters, and get a good idea of how WCF-based services process messages**. 

## FileAct and InterAct
The [!INCLUDE[swift_adapter_md](../includes/swift-adapter-md.md)] are included with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and provide connectivity between your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] and the Society for Worldwide Interbank Financial Telecommunication (SWIFT) Secure IP Network (SIPN). 

The FileAct adapter provides secure and reliable exchange of files, and information pertaining to those files. 

The InterAct adapter provides secure and reliable exchange of individual structured financial messages. 

**See [FileAct and InterAct](../adapters-and-accelerators/fileact-interact/microsoft-biztalk-server-fileact-and-interact-adapters-documentation.md) to install and configure these adapters, step through some tutorials and scenarios, and get a good understanding of the architecture**. 

## HL7

The [!INCLUDE[btaBTAHL7NoNumber_md](../includes/btabtahl7nonumber-md.md)] is included with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and provides connectivity between your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] and health care computer applications based on the Health Level Seven (HL7) standard.

**See [HL7](../adapters-and-accelerators/accelerator-hl7/microsoft-biztalk-accelerator-for-hl7-documentation.md) to install and configure the adapter, step through several tutorials and scenarios, learn how the adapter works, and use the different features, including schemas, acknowledgments, batching, validation, and more**.

## RosettaNet
The BizTalk Accelerator for RosettaNet (BTARN) is included with BizTalk Server, and streamlines the development and deployment of RosettaNet standards-based integration solutions. BTARN supports the RosettaNet Implementation Framework (RNIF); which is an open network application framework that enables business partners to collaboratively run RosettaNet Partner Interface Processes (PIPs). 

**See [RosettaNet](../adapters-and-accelerators/accelerator-rosettanet/microsoft-biztalk-accelerator-for-rosettanet-documentation.md) to learn more about this accelerator, and using it with your BizTalk Server solutions.** 

## SWIFT
The [!INCLUDE[btaA4SWIFTNoVersion_md](../includes/btaa4swiftnoversion-md.md)] is included with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and provides connectivity between your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] and the Society for Worldwide Interbank Financial Telecommunication (SWIFT) message formats.

Using the adapter with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], customers, partners, and system integrators can streamline the development, deployment, and support of integration solutions for core financial services application infrastructure and business processes.

**See [SWIFT](../adapters-and-accelerators/accelerator-swift/microsoft-biztalk-accelerator-for-swift-documentation.md) to install and configure the adapter, step through some tutorials, and use the message repair, FIN response and FRR artifacts, and more**.

## Get some help 
Get some help, and help others in the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] forums [http://go.microsoft.com/fwlink/p/?LinkId=87695](http://go.microsoft.com/fwlink/p/?LinkId=87695).