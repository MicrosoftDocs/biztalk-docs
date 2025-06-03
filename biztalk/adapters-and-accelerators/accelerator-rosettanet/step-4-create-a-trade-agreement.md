---
description: "Learn more about: Step 4: Create a Trade Agreement"
title: "Step 4: Create a Trade Agreement"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Step 4: Create a Trade Agreement
In this step, you create a trade agreement between the home and partner organization using the Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console.  

### To create a trade agreement  

1. In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand **BizTalk \<version\> Accelerator for RosettaNet**, right-click **Agreements**, click **New**, and then click **Agreement**.  

2. In the **New Agreement Properties** dialog box, on the **General** tab, do the following:  


   |         Use this          |                     To do this                     |
   |---------------------------|----------------------------------------------------|
   |         **Name**          |             Type **Trade Agreement**.              |
   | **Process Configuration** | Select **STD_0C1_R01.02** from the drop-down list. |
   |    **My organization**    |      Select **HOME** from the drop-down list.      |
   | **Partner organization**  |    Select **PARTNER** from the drop-down list.     |
   |       **Home role**       |   Select **Initiator** from the drop-down list.    |


3. In the **New Agreement Properties** dialog box, on the **Ports** tab, do the following:  


   |    Use this    |                                         To do this                                         |
   |----------------|--------------------------------------------------------------------------------------------|
   | **Action URL** |                   Type `http://localhost/BTARNApp/RNIFReceive.aspx`                   |
   | **Signal URL** |                   Type `http://localhost/BTARNApp/RNIFReceive.aspx`                   |
   |  **Sync URL**  | Leave blank. Sync URL is not required for the synchronous Partner Interface Process (PIP). |


4. Click **Apply**, and then click **OK**.  

   After you create the trade agreement, you must activate it.  

### To activate the trade agreement  

- In the [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], click **Agreements**, right-click **Trade Agreement** in the results pane, and then click **Activate**.  

## See Also  
 [Step 5: Create a Mirror Agreement](../../adapters-and-accelerators/accelerator-rosettanet/step-5-create-a-mirror-agreement.md)
