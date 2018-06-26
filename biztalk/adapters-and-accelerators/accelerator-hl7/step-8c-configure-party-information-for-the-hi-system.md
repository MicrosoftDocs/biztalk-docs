---
title: "Step 8C: Configure Party Information for the HI System | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ac5c113-7ee7-4009-8ca3-d263f74c7a8d
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 8C: Configure Party Information for the HI System
In this step, you configure the party information for the HI System.  

### To configure the HI System party information  

1. In the BizTalk Server Administration Console, right-click **Parties**, point to **New**, and then click **Party**.  

2. In the Party Properties dialog box, in the **Name** box, type **Tutorial_HISystem**.  

3. In the console tree, click **Send Ports**.  

4. In the Send Ports pane, click the blank field in the **Name** column, select **Tutorial_MllpSend**, and then click **OK**.  

5. Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.  

6. In BTAHL7 Configuration Explorer, select the **MSH Map** tab, and then do the following:  


   | Use this  |                                             To do this                                             |
   |-----------|----------------------------------------------------------------------------------------------------|
   | **MSH3**  | Type **BTAHL7**, **IE**, and **UUID** in the first, second, and third message boxes, respectively. |
   | **MSH5**  | Type **HI**, **System**, and **GUID** in the first, second, and third message boxes, respectively. |
   | **MSH9**  |           Type **ADT** and **A04** in the first and second message boxes, respectively.            |
   | **MSH12** |                                           Type **2.4**.                                            |
   | **MSH15** |         Select **SU** to send acknowledgments after successful transmission of a message.          |
   | **MSH16** |                            Select **NE** to never send acknowledgments.                            |


7. Click **Save**, and then close the BTAHL7 Configuration Explorer.  

   > [!NOTE]
   >  You do not need to create party information for the BTAHL7 Interface Engine System, because configuration information is not required for this scenario.  

   Proceed to [Step 9: Restart BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md).