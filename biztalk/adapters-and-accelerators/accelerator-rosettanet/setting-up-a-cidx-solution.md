---
title: "Setting Up a CIDX Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CIDX, process configuration"
  - "creating, CIDX solutions"
  - "CIDX, connecting to Elemica network"
  - "agreements, CIDX"
  - "process configuration, CIDX"
  - "CIDX, agreements"
  - "PIPs, importing for CIDX"
  - "CIDX, PIPs"
  - "CIDX, creating solutions"
  - "CIDX, importing PIPs"
  - "PIPs, CIDX"
ms.assetid: 7f1f159f-3b09-4efd-907b-9a75f7f3ecd1
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Setting Up a CIDX Solution
Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] support for CIDX (Chemical Industry Data Exchange) XML message exchange (CIDX Chem eStandards versions 2.0 and 3.0). This topic describes how to set up a CIDX solution by doing the following:  
  
-   Setting up a process configuration  
  
-   Setting up an agreement  
  
-   Applying a PIP  
  
-   Importing an XSD-based PIP  
  
-   Connecting to the Elemica Network  
  
## Setting Up a CIDX Process Configuration  
 To set up a CIDX eStandards message exchange, you need to create a process configuration that has the following properties:  
  
- **Standard** property in the process configuration settings set to **CIDX**  
  
- **Is Single Action** property in the process configuration settings set to **True**  
  
- **0A1 agreement** property in the trading partner agreement set to **No 0A1**  
  
  For more information, see [Setting Up CIDX eStandards Message Exchange](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md).  
  
## Creating a CIDX Agreement  
 To set up a CIDX eStandards message exchange, you need to create an agreement that has the following properties:  
  
- **RNIF Version** property in the agreement settings set to **V01.10.00**  
  
- **0A1 agreement** property in the agreement settings set to **No 0A1**  
  
  For more information, see [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).  
  
## Applying a PIP for CIDX  
 To apply a PIP to a CIDX implementation, set the **Standard** property in the process configuration profile to **CIDX**. After you have finished, you will be able to enter values for the **Message standard**, **Standard version**, and **Payload binding ID**. You can find these values in the CIDX Chem eStandards specification.  
  
## Importing an XSD-based PIP for CIDX  
 To import an XSD-based PIP for CIDX, you need to download the PIP's ZIP file from CIDX.org at [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=62361). Follow the import procedure described in [Importing an XSD-based PIP](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md).  
  
## Connecting to the Elemica Network  
 You can customize [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] to connect to Elemica using project files in the Elemica Connectivity Pack. You can download the Connectivity Pack from [http://go.microsoft.com/fwlink/?LinkId=46195](http://go.microsoft.com/fwlink/?LinkId=46195). For more information, see the “Connecting to the Elemica Network with BizTalk Accelerator for RosettaNet 3.0” white paper on MSDN at [http://go.microsoft.com/fwlink/?linkid=46539](http://go.microsoft.com/fwlink/?linkid=46539).  
  
> [!NOTE]
>  The information in the "Connecting to the Elemica Network with BizTalk Accelerator for RosettaNet 3.0" white paper is valid for [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)].  
  
## See Also  
 [CIDX Support](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md)   
 [CIDX Messaging Standards](../../adapters-and-accelerators/accelerator-rosettanet/cidx-messaging-standards.md)   
 [Setting Up CIDX eStandards Message Exchange](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)   
 [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)   
 [Importing an XSD-based PIP](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md)