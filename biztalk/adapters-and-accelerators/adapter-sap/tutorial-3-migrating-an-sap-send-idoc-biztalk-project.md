---
title: "Tutorial 3: Migrating an SAP Send IDOC BizTalk Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "migrating, SAP Send IDOC BizTalk project"
  - "migration"
ms.assetid: c0a11432-5388-4054-8996-08a957cc02eb
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tutorial 3: Migrating an SAP Send IDOC BizTalk Project
The previous version of the SAP adapter that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in many aspects, including:  
  
- The design-time experience of creating a BizTalk project.  
  
- The metadata retrieval experience.  
  
- Schema file name and namespace.  
  
- Data type mappings.  
  
- The operations that can be performed using the adapter.  
  
- Physical port configuration in the BizTalk Server Administration console.  
  
  These differences are explained in the topics within [Migrating BizTalk Projects Created Using the Previous Version of the SAP Adapter](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37).  
  
  However, you can make changes to the BizTalk project created using the previous version of the adapter and make it work with the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
  This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the previous version of the adapter.  
  
> [!NOTE]
>  In this tutorial, for the sake of brevity, the previous version of the SAP adapter will be referred to as vPrev SAP adapter. Similarly, a BizTalk project that uses the vPrev SAP adapter will be referred to as vPrev BizTalk project.  
  
## Sample Used for the Tutorial  
 This tutorial is based upon a sample (SendIDOC_Migration) that demonstrates how to migrate a vPrev BizTalk project that sends an IDOC to an SAP system. The sample is provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## Prerequisites  
  
-   You must have a vPrev BizTalk project. This tutorial involves a BizTalk project that sends a BOMDOC IDOC to an SAP system.  
  
-   You must have a flat-file BOMDOC IDOC to send to the SAP system using the vPrev SAP adapter. The sample provided for this tutorial contains this flat-file IDOC.  
  
-   [Create strong-name key file, and learn the tools](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)
  
## Understanding a BizTalk Project Created Using the Previous Version of the Adapter  
 The key constituents of a vPrev BizTalk project to send an IDOC are:  
  
-   **BizTalk orchestration**. This is a simple orchestration that picks a flat-file IDOC from a file location and sends the IDOC to the SAP system using an SAP send port. The BizTalk project contains a flat-file disassembler to convert the flat-file IDOC to an XML, so that it can be used in an orchestration. Before the XML IDOC is consumed by the vPrev SAP send port, it is converted back into a flat-file IDOC using a flat-file assembler.  
  
-   **Schema for the IDOC you want to send to the SAP system**. For this tutorial, you take a BizTalk project that sends BOMDOC01 IDOC to the SAP system. The schema generated for the IDOC is BOMDOC01.xsd. This schema is generated using the vPrev SAP adapter.  
  
-   **The flat-file IDOC**. This is the flat-file IDOC that is sent to the SAP system.  
  
## How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter  
 The goal of this migration tutorial is to enable you to send a flat-file IDOC to an SAP system using a WCF-Custom send port instead of the send port for the vPrev SAP adapter. Before understanding what settings are required for the WCF-Custom send port, you must first understand what physical ports are required for the vPrev send IDOC orchestration:  
  
- A file receive port that picks the flat-file IDOC. This port uses the flat-file disassembler pipeline, available in the BizTalk application, to convert the flat-file into an XML that conforms to the schema (BOMDOC01.xsd) generated using the vPrev SAP adapter.  
  
- A vPrev SAP send port that sends the flat-file IDOC to the SAP system. Before sending the flat-file, the port uses the flat-file assembler to convert the XML IDOC into a flat-file IDOC.  
  
  To migrate your existing vPrev BizTalk project, you do not need to change the file receive port that picks the flat-file IDOC and converts the flat-file IDOC to XML using a flat-file disassembler. You only need to configure a new WCF-Custom send port with the right configuration settings. This tutorial demonstrates how to configure the WCF-Custom send port to send IDOCs to an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## In This Section  
  
-   [Step 1: Build and Deploy the vPrev BizTalk Project for Sending an IDOC](../../adapters-and-accelerators/adapter-sap/step-1-build-and-deploy-the-vprev-biztalk-project-for-sending-an-idoc.md)  
  
-   [Step 2: Configure a WCF-Custom One-way Send Port](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-send-port.md)  
  
-   [Step 3: Test the Migrated Application](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application2.md)  
  
## See Also  
 [SAP Adapter Tutorials](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)