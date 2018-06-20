---
title: "Step 4: Creating the Fabrikam 0C4 Trading Partner Agreement | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "double action tutorial, creating agreements"
ms.assetid: a99c2cd1-0d42-4fae-a380-a53d77cd87d0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 4: Creating the Fabrikam 0C4 Trading Partner Agreement
In this step, you create a trading partner agreement between Contoso and Fabrikam using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console. You create a new trading partner agreement for the 0C4 Partner Interface Process (PIP).  

### To start the BTARN Management Console  

- Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.  

### To create the 0C4 trading partner agreement  

1. In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Agreements**, point to **New**, and then click **Agreement**.  

2. In the New Agreement Properties dialog box, on the **General** tab, do the following:  


   |         Use this          |                        To do this                         |
   |---------------------------|-----------------------------------------------------------|
   |         **Name**          |             Type **Fabrikam_To_Contoso_0C4**.             |
   | **Process Configuration** |    Select **STD_0C4_R01.02** from the drop-down list.     |
   |    **My Organization**    |       Select **Fabrikam** from the drop-down list.        |
   | **Partner Organization**  |        Select **Contoso** from the drop-down list.        |
   |     **RNIF Version**      |       Select **V02.00.01** from the drop-down list.       |
   |       **Home Role**       | Select **Initiator (Initiator)** from the drop-down list. |
   |         **Usage**         |         Select **Test** from the drop-down list.          |


3. Click the **Ports** tab, and then do the following:  


   |    Use this    |                          To do this                           |
   |----------------|---------------------------------------------------------------|
   | **Action URL** | Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**. |
   | **Signal URL** | Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**. |
   |  **Sync URL**  | Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**. |


4. Click **OK**.  

5. Right-click the **Fabrikam_To_Contoso_0C4** agreement, and then click **Activate**.  

## See Also  
 [Step 5: Creating the Fabrikam 3A2 Trading Partner Agreement](../../adapters-and-accelerators/accelerator-rosettanet/step-5-creating-the-fabrikam-3a2-trading-partner-agreement.md)