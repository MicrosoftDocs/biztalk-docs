---
description: "Learn more about: Step 3: Create the Request Decline Schema"
title: "Step 3: Create the Request Decline Schema"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 3: Create the Request Decline Schema
![Step 3 of 5](../core/media/step-3of5.gif "Step_3of5")  
  
 **Time to complete:** 7 minutes  
  
 **Objective:** In this step, you create the schema for the message [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends back to the warehouse if the business process rejects the inventory replenishment request.  
  
 **Purpose:** The schema defines the data and the structure of the request decline message. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the schema to identify and interact with the data in the message.  
  
## Prerequisites  
 Note the following requirements before you begin this step:  
  
-   Before you begin this step you must complete [Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md).  
  
## Procedures  
  
#### To create the Request Decline schema  
  
1.  In Solution Explorer, right-click the **EAISchemas** project, point to **Add**, and then click **New Item**.  
  
2.  In the **Add New Item - EAISchemas** dialog box, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Installed Templates**|Click **Schema Files**, and then click **Schema**.|  
    |**Name**|Type `RequestDecline.xsd`.|  
  
3.  Click **Add**.  
  
4.  In BizTalk Editor, from schema tree, click the **Root** node to select it.  
  
5.  In the Properties pane, change the value of the **Node Name** property to `DeclineReq`, and then press ENTER.  
  
6.  In schema tree, right-click the **DeclineReq** node, point to **Insert Schema Node**, and then click **Child Field Element**.  
  
7.  Type `ReqID` as the new name for the element, and then press ENTER.  
  
8.  Add a second child field element named `GrandTotal`.  
  
9. On the **File** menu, click **Save All**.  
  
## What did I just do?  
 In this step, you created the schema for the message that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends back to the warehouse if the business process rejects the inventory request.  
  
## Next Steps  
 You create the map needed by the orchestration to create request decline message by reformatting request message.  
  
## See Also  
 [Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md)  
 [Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md)   
 [Step 4: Create the Map](../core/step-4-create-the-map.md)   
 [Step 5: Build the EAISchemas Project](../core/step-5-build-the-eaischemas-project.md)   
 [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md)
