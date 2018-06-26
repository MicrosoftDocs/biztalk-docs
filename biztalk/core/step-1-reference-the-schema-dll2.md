---
title: "Step 1: Reference the Schema DLL2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1db92227-6164-42b9-b60c-12dd2cae46e2
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Reference the Schema DLL
In BizTalk, messages are immutable. Therefore, to change a property value you must create and modify a new message. You create and modify the new message by inserting a message assignment shape between the Receive and Send shapes.  
  
 First, however, you must reference the schema DLL to gain access to the J.D. Edwards context properties.  
  
### To reference the schema DLL  
  
1. Create a working folder, for example, c:\class\JDE\BeginDoc, for your project and a folder in which you will put the test XML, for example, c:\class\JDE\input.  
  
2. Create a Static Solicit-Response Send Port to send the request to J.D. Edwards OneWorld.  
  
    ![](../core/media/jde-example-2waysendport-ow.gif "JDE_example_2waysendport_OW")  
  
3. In the Solution Editor, right-click your project.  
  
   1. Select **Add**, select **Add Generated Items**, and then click **Add Adapter**.  
  
   2. Select the Microsoft BizTalk Adapter for J.D. Edwards OneWorld and the port you just created.  
  
   3. In the **Add Adapter Wizard**, select **CSALES\B4200310**.  
  
   4. Click **Finish** to generate the schema containing the format for the Message.  
  
      ![](../core/media/jde-add-adapter-wizard.gif "JDE_add_adapter_wizard")  
  
4. In Visual Studio, open the Solution Explorer.  
  
5. Right-click **References**, and then select **Add Reference**.  
  
6. On the **Add Reference** screen, click the **Browse** button.  
  
    ![](../core/media/jde-add-reference-dll.gif "JDE_add_reference_dll")  
  
7. On the **Select Component** screen, navigate to %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.  
  
8. Select **Microsoft.Adapters.JDEProperties.dll**, and then click **Open**.  
  
9. On the **Add Reference** screen, the DLL appears in the **Selected Components** section.  
  
     ![](../core/media/jde-properties-selection.gif "JDE_properties_selection")  
  
10. Click **OK**.  
  
11. Double-click your orchestration to access the Orchestration Designer.  
  
     \- OR -  
  
     Select **View**, select **Other Windows**, and then click **Orchestration View**.  
  
     The Orchestration View appears.  
  
## See Also  
 [Step 2: Create the Orchestration](../core/step-2-create-the-orchestration1.md)   
 [Step 3: Complete and Run the Project](../core/step-3-complete-and-run-the-project2.md)   
 [Step 4: Create a Sample XML BeginDoc](../core/step-4-create-a-sample-xml-begindoc1.md)