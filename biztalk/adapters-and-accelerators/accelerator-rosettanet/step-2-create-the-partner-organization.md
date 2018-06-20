---
title: "Step 2: Create the Partner Organization | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "partner organization"
  - "trading partners, partner organization"
  - "loopback tutorial, creating partner organization"
ms.assetid: 489bc961-dcb6-4610-989d-c06ba9f71b02
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Create the Partner Organization
In this step, you create the partner organization using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console.  

### To create the partner organization  

1. In the  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand **BizTalk \<version\> Accelerator for RosettaNet**, right-click **Partners**, click **New**, and then click **Partner**.  

2. In the **New Partner Properties** dialog box, do the following:  


   | Use this |     To do this      |
   |----------|---------------------|
   | **Name** |  Type **PARTNER**.  |
   | **GBI**  | Type **987654321**. |


3. In the **New Partner Properties** dialog box, on the **Contact Properties** tab, do the following:  


   |       Use this        |                To do this                |
   |-----------------------|------------------------------------------|
   |   **Contact Name**    |            Type **Jane Doe**.            |
   |  **E-mail Address**   | Type <strong>jdoe@fabrikam.com</strong>. |
   | **Telephone Number**  |          Type **555-555-5555**.          |
   |    **Fax Number**     |          Type **555-555-5555**.          |
   | **Supply chain code** |     Type **Electronic Components**.      |


4. Click **Apply**, and then **OK**.  

> [!NOTE]
>  If you have an encryption certificate, you configure it here. For information about configuring encryption certificates, see [Managing Certificates](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md).  

## See Also  
 [Step 3: Edit the Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/step-3-edit-the-partner-interface-process.md)