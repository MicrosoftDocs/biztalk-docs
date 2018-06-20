---
title: "Step 7: Create a Send Port to Deliver Response Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interrogative tutorial, send ports"
ms.assetid: 5edaefb6-72f2-4317-9477-f3a0d0027e0c
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 7: Create a Send Port to Deliver Response Messages
In this step, you create the send port to deliver the query responses back to the Admissions, Discharge, and Transfer (ADT) system.  

### To create the ADT_Send send port  

1. In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then select **Static One-way Send Port**.  

2. In the Send Port Properties dialog box, do the following:  


   |      Use this      |                        To do this                        |
   |--------------------|----------------------------------------------------------|
   |      **Name**      |                    Type **ADT_Send**.                    |
   | **Transport type** |                     Select **MLLP**.                     |
   |   **Configure**    | Click the **Configure** button to the right of **Type**. |


3. In the MLLP Transport Properties dialog box, enter the following information, and then click **OK**.  


   |      Use this       |       To do this       |
   |---------------------|------------------------|
   | **Connection Name** | Type **ADT_SendMLLP**. |
   |      **Host**       |  Type **localhost**.   |
   |      **Port**       |    Type **25000**.     |


4. In the Send Port Properties dialog box, for **Send Pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.  

5. In the Console Tree, click **Filters**, and then do the following:  


   |   Use this   |                                        To do this                                        |
   |--------------|------------------------------------------------------------------------------------------|
   | **Property** |                               Select **BTS.MessageType**.                                |
   | **Operator** |                          Select **==** from the drop-down list.                          |
   |  **Value**   |          Type **<http://microsoft.com/HealthCare/HL7/2X#DSR_Q01_24_GLO_DEF>**.           |
   | **Group By** |                         Select **AND** from the drop-down list.                          |
   | **Property** | Under the first property, click the blank box, and then select **BTAHL7Schemas.MSH5_1**. |
   | **Operator** |                          Select **==** from the drop-down list.                          |
   |  **Value**   |                                      Type **ADT**.                                       |

   > [!NOTE]
   >  The first filter specifies that the send port only selects messages conforming to the DSR^Q01 schema you created in step 3A. The second filter specifies the destination to which the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine sends these messages.  

6. Click **OK**.  

7. In the Administration Console, click **Send Ports**, right-click **ADT_Send**, and then click **Start**.  

   Proceed to [Step 8: Configure Party Information](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information-hl7-main.md).