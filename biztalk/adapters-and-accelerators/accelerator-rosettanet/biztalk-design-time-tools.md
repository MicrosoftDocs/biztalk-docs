---
title: BizTalk design-time tools
description: Learn about the BizTalk design-time tools.
ms.service: biztalk-server
ms.topic: article
ms.date: 06/08/2017
---

# BizTalk design-time tools

Developers working on Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] can use the set of design-time tools built into BizTalk Server. These tools are integrated into Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]. For more information about [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools, see MicrosoftBizTalk Server Help.

## BizTalk Editor
 You use BizTalk Editor to manage [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] XSD schemas that are based on RosettaNet Partner Interface Processes (PIPs). [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] installs the following schemas for your solution development:

- 0A1_FailureNotificationPropertySchema.xsd

- 0A1_MS_V02_00_FailureNotification.xsd

- 0A1_V1_FailureNotificationMessageGuideline.xsd

- 0C1_MS_R01_02_AsynchronousTestNotification.xsd

- 0C2_MS_R01_02_AsynchronousTestConfirmation.xsd

- 0C2_MS_R01_02_AsynchronousTestRequest.xsd

- 0C3_MS_R01_02_SynchronousTestNotification.xsd

- 0C4_MS_R01_02_SynchronousTestQuery.xsd

- 0C4_MS_R01_02_SynchronousTestResponse.xsd

- 2A12_MS_V01_03_ProductMasterNotification.xsd

- 3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.xsd

- 3A2PriceAndAvailabilityResponseMessageGuideline_v1_3.xsd

- 3A4_MS_V02_02_PurchaseOrderConfirmation.xsd

- 3A4_MS_V02_02_PurchaseOrderRequest.xsd

  These schemas are available at \<*drive*\>:\Program Files\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK\Schemas.

  You can add more schemas by downloading PIPs from the [GS1 US RosettaNet Standards website](https://www.gs1us.org/resources/rosettanet). For more information, see [Incorporating a New Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md).

## BizTalk Mapper
 You use BizTalk Mapper to create and customize maps that define data transformations. You use BizTalk Mapper to map transformations for both inbound and outbound RosettaNet message types.

## BizTalk Orchestration Designer
 You use BizTalk Orchestration Designer to design and implement business processes. You can customize the private processes provided in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK. For more information, see [Private Processes &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md) and [Customizing Private Processes &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/customizing-private-processes.md). You cannot customize public processes; doing this would invalidate their RosettaNet compliance.

## BizTalk Pipeline Designer
 You use BizTalk Pipeline Designer to create and configure the pipelines that define and link message-processing steps. Pipelines divide message processing into stages, and determine the sequence in which you perform each category of work.

 The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes both receive and transmit RosettaNet Implementation Framework (RNIF) pipelines. For more information, see [RNIF Pipelines](../../adapters-and-accelerators/accelerator-rosettanet/rnif-pipelines.md).

## BizTalk Adapter Framework
 You use the BizTalk Adapter Framework with end-point adapters to integrate with partners and applications.

## See also
[Tools and Features of BizTalk Server and BTARN](../../adapters-and-accelerators/accelerator-rosettanet/tools-and-features-of-biztalk-server-and-btarn.md)
[Administration and Run-Time Tools](../../adapters-and-accelerators/accelerator-rosettanet/administration-and-run-time-tools.md)
[Analysis Tools](../../adapters-and-accelerators/accelerator-rosettanet/analysis-tools1.md)
[Incorporating a New Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)
