---
title: "Step 2: Creating the Contoso Partner Organization | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "double action tutorial, creating partner organizations"
ms.assetid: ebb3b166-3781-40b9-89d4-2ca0c83d05f3
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Creating the Contoso Partner Organization
In this step, you use the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console to create a new trading partner. The trading partner for this tutorial is the Contoso organization.  

### To start the BTARN Management Console  

- Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.  

### To create Fabrikam as a trading partner  

1. In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Partners**, point to **New**, and then click **Partner**.  

2. In the New Partner Properties dialog box, on the **General** tab, do the following<strong>:</strong>  


   |          Use this          |                             To do this                              |
   |----------------------------|---------------------------------------------------------------------|
   |          **Name**          |                          Type **CONTOSO**.                          |
   |          **GBI**           |                         Type **123456789**.                         |
   | **Partner Classification** |          Select **Manufacturer** from the drop-down list.           |
   | **Signature Certificate**  | Select **Contoso Signature [Thumbprint]** from the drop-down list.  |
   | **Encryption Certificate** | Select **Contoso Encryption [Thumbprint]** from the drop-down list. |


3. Click the **Contact Properties** tab, and then do the following:  


   |       Use this        |               To do this                |
   |-----------------------|-----------------------------------------|
   |   **Contact Name**    |           Type **John Doe**.            |
   |  **E-mail Address**   | Type <strong>jdoe@contoso.com</strong>. |
   | **Telephone Number**  |         Type **555-555-5555**.          |
   |    **Fax Number**     |         Type **555-555-5555**.          |
   | **Supply chain code** |     Type **Electronic Components**.     |


4. Click **OK**.  

## See Also  
 [Step 3: Creating the Fabrikam 0C2 Trading Partner Agreement](../../adapters-and-accelerators/accelerator-rosettanet/step-3-creating-the-fabrikam-0c2-trading-partner-agreement.md)