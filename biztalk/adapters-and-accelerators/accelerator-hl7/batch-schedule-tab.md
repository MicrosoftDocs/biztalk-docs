---
description: "Learn more about: Batch Schedule Tab"
title: "Batch Schedule Tab"
ms.date: "06/08/2017"
ms.prod: biztalk-server
ms.topic: article
f1_keywords: 
  - "btahl7.configurationexplorer.tab.batchschedule"
---
# Batch Schedule Tab
You use the **Batch Schedule** tab to activate, request, or terminate an outbound batch. Activating an outbound batch consists of two steps: configuring time-based or message count criteria and then starting the outbound batching orchestration.  
  
 You can configure [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to create an outbound batch using time-based or message count criteria or a combination of both. Setting batch activation criteria is optional. If not specified, you can activate a batch manually. If you want to activate a batch using time-based or message count criteria, you must specify these criteria before activating the batch.  
  
 In the **BTAHL7 Configuration Explorer** dialog box, on the **Batch Schedule** tab, do the following:  
  
|Use this|To do this|  
|--------------|----------------|  
|**Hours before first batch**|Type the number of hours before starting the first batch.<br /><br /> This option is not available when you select message count as the batch control.|  
|**Repeat Batch After**|Select one of the following options:<br /><br /> -                   **Hours**. Type the number of hours to wait before repeating the batch process.<br /><br /> -                   **Messages**. Type the number of messages that you want to process before initiating the next batch.|  
|**Batch Control**|Use the following options:<br /><br /> -                   **Start Schedule**: Select this option to start your batch schedule.<br /><br /> -                   **Send Now**: Select this option to start the batch process immediately. This overrides the **Hours before first batch** and **Repeat Batch After** settings.<br /><br /> -                   **Stop Schedule**: Select this option to stop the current batch schedule. This completes the current batch and then stops the batch orchestration.|
