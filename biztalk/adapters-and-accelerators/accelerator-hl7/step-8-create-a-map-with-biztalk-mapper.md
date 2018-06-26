---
title: "Step 8: Create a Map with BizTalk Mapper | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message enrichment tutorial, maps"
  - "creating, maps"
  - "maps, creating"
  - "BizTalk Mapper"
ms.assetid: 785426c7-5651-48be-b3f4-7f9d8051ba23
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 8: Create a Map with BizTalk Mapper
In this step, you use the BizTalk Mapper to create a map. You use this map to create links that associate the data (fields) in a replenishment request document to the data in a request denied document.  
  
### To create a map  
  
1. In Solution Explorer, right-click **BTAHL7 Project**, point to **Add**, and then click **New Item**.  
  
2. In the **Add New Item** dialog box, in the **Categories** pane, click **Map Files**.  
  
3. In the **Name** field, type **DoorbellMap** to name the map, and then click **Add** to start BizTalk Mapper.  
  
4. In the **Source Schema** pane (left side), click **Open Source Schema**.  
  
5. In the BizTalk Type Picker dialog box, expand **BTAHL7 Project**, expand **Schemas**, click **BTAHL7_Project.Doorbell**, and then click **OK**.  
  
6. In the **Destination Schema** pane (right side), click **Open Destination Schema**.  
  
7. In the BizTalk Type Picker, expand **BTAHL7 Project**, expand **Schemas**, click **BTAHL7Schemas.ADT_A04_22_GLO_DEF**, and then click **OK**.  
  
8. In the **Destination Schema** pane (right side), expand **ADT_A04_22_GLO_DEF**, expand **PID_PatientIdentification**, and expand **PID.5_PatientName**.  
  
9. In the **Source Schema** pane (left side), expand **DoorbellRoot**. Drag the **LastName** field to the **PN_0_FamilyName** field in the **Destination Schema** pane.  
  
10. In the **Source Schema** pane, drag the **FirstName** field to the **PN_1_GivenName** field in the **Destination Schema** pane.  
  
11. In the **Source Schema** pane, drag the **MiddleName** field to the **PN_2_MiddleInitialOrName** field in the **Destination Schema** pane.  
  
12. In the **Destination Schema** pane, expand **PID_3_PatientIdInternalId**.  
  
13. In the **Source Schema** pane, drag the **SSN** field to the **CM_PAT_ID_0_PatientID** in the **Destination Schema** pane.  
  
14. In the **File** menu, click **Save All**.  
  
    In a typical message enrichment scenario, if any patient information were missing, you would make a call to a Patient Records database in your orchestration and add the missing information, then use the additional information to complete the mapping. For example, you might retrieve the home address of a patient from the Patient Records database, since the inbound XML doorbell trigger event message did not provide it.  
  
    Proceed to [Step 9: Validate and Build the Map Project](../../adapters-and-accelerators/accelerator-hl7/step-9-validate-and-build-the-map-project.md).  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)