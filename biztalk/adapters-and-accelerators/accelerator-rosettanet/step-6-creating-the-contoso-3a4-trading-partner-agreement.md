---
title: "Step 6: Creating the Contoso 3A4 Trading Partner Agreement | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "agreements, creating"
  - "creating, agreements"
  - "double action tutorial, creating agreements"
ms.assetid: a20e40d8-7e3b-4930-8921-056ffddd08ea
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 6: Creating the Contoso 3A4 Trading Partner Agreement
In this step, you create a trading partner agreement between Contoso and Fabrikam using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console. You create a new trading partner agreement for the 3A4 Partner Interface Process (PIP).  

### To start the BTARN Management Console  

- Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.  

### To create the 3A4 trading partner agreement  

1. In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Agreements**, point to **New**, and then click **Agreement**.  

2. In the New Agreement Properties dialog box, on the **General** tab, do the following:  


   |         Use this          |                       To do this                       |
   |---------------------------|--------------------------------------------------------|
   |         **Name**          |           Type **Fabrikam_To_Contoso_3A4**.            |
   | **Process Configuration** |   Select **STD_3A4_V02.02** from the drop-down list.   |
   |    **My Organization**    |      Select **Contoso** from the drop-down list.       |
   | **Partner Organization**  |      Select **Fabrikam** from the drop-down list.      |
   |     **RNIF Version**      |     Select **V02.00.01** from the drop-down list.      |
   |       **Home Role**       | Select **Seller (Responder)** from the drop-down list. |
   |         **Usage**         |        Select **Test** from the drop down-list.        |


3. On the **Ports** tab, do the following:  


   |    Use this    |                          To do this                           |
   |----------------|---------------------------------------------------------------|
   | **Action URL** | Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx** |
   | **Signal URL** | Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx** |
   |  **Sync URL**  | Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx** |


4. Click **OK**.  

5. Right-click the **Fabrikam_To_Contoso_3A4** agreement and then click **Activate**.  

## See Also  
 [Step 7: Building and Deploying the DoubleAction SDK Sample](../../adapters-and-accelerators/accelerator-rosettanet/step-7-building-and-deploying-the-doubleaction-sdk-sample.md)