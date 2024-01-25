---
description: "Learn more about: Step 9: Validate and Build the Map Project"
title: "Step 9: Validate and Build the Map Project"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: article
---
# Step 9: Validate and Build the Map Project
In this step, you use the **Validate Map** command to determine if the map contains any internal inconsistencies, or has other issues that would prevent it from being used effectively for mapping schemas. You also build the project to generate an assembly that contains the resources (schemas and the map) that you created. This also ensures that there are no compile errors in the work that you have completed so far.  
  
### To validate the map project  
  
1.  In Solution Explorer, right-click the **DoorbellMap.btm** map, and then click **Validate Map**.  
  
2.  Ensure that a success message appears in the output window. Some warnings may appear because you are not mapping to all available elements in the destination schema.  
  
     If no success message appears, troubleshoot the map project.  
  
### To build the map project  
  
- In Solution Explorer, right-click **BTAHL7 Project**, and then click **Build**. Ensure that a success message appears in the output window.  
  
   If no success message appears, troubleshoot the map project.  
  
  Proceed to [Step 10: Create an Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-10-create-an-orchestration.md).  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)
