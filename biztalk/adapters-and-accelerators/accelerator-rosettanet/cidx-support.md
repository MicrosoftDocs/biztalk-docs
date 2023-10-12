---
description: "Learn more about: CIDX Support"
title: "CIDX Support"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# CIDX Support
Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] provides support for CIDX (Chemical Industry Data Exchange) XML message exchange. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] supports CIDX Chem eStandards versions 2.0 and 3.0, both of which use the RosettaNet Implementation Framework (RNIF) 1.1.

 The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] asynchronous simple public processes (supporting single-action and double-action messages) consume and route CIDX service content.

 For an agreement based on a CIDX PIP, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will validate the following in a message:

- RNIF 1.1 version only

- No 0A1

- Only Single Action

  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will not prevent you from setting the `Standard` property for a process configuration to "CIDX", after you have set the `0A1 agreement` property for an agreement that uses that profile to "0A1" (which is not supported for CIDX). [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not perform the cross-field validation that would prevent this.

## Applying a PIP to a CIDX Implementation
 To apply a PIP to a CIDX implementation, set the `Standard` property in the process configuration profile to **CIDX**. After you have finished, you will be able to enter values for the Message standard, Standard version, and Payload binding ID. You can find these values in the CIDX Chem eStandards specification.

## Connecting to the Elemica Network
 You can enable an installation of Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] to connect to the Elemica [!INCLUDE[btsExchangeSvrNoVersion](../../includes/btsexchangesvrnoversion-md.md)] Provider (ESP). You can use the Elemica network for chemical-industry buying, selling, and supply-chain management using CIDX message exchange.

 You customize [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] to connect to Elemica using project files in the Elemica Connectivity Pack. You can download the Connectivity Pack at [https://go.microsoft.com/fwlink/?LinkId=46195](https://go.microsoft.com/fwlink/?LinkId=46195). 

For more connection information and details, go to [How to Connect to the Elemica Network with BizTalk Accelerator for RosettaNet](https://social.technet.microsoft.com/wiki/contents/articles/232.how-to-connect-to-the-elemica-network-with-biztalk-accelerator-for-rosettanet.aspx).

## CIDX Procedures
 The following sections described how to set up CIDX message exchange:

-   [Setting Up CIDX eStandards Message Exchange](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)

-   [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)

-   [Importing an XSD-based PIP](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md)

## See Also
 [What BizTalk Accelerator for RosettaNet Adds to BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)
 [CIDX Messaging Standards](../../adapters-and-accelerators/accelerator-rosettanet/cidx-messaging-standards.md)
