---
title: "Tutorial: Use TIBCO EMS Message Context Properties"
description: step-by-step guide to use the TIBCO Enterprise Message Service message descriptor fields in your orchestration for BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: tutorial
---
# Tutorial: Use TIBCO EMS message descriptors

## Overview
This tutorial demonstrates how to use BizTalk Server context properties to set TIBCO Enterprise Message Service (EMS) message descriptor fields in your orchestration. The tutorial assumes that you have an orchestration that receives a message from a receive port and sends the message to a send port bound to Microsoft BizTalk Adapter for TIBCO Enterprise Message Service.  
  
 The following procedure demonstrates how to change the priority of the TIBCO EMS message by changing the value of the TibcoEMS.Priority context property. In BizTalk Server, messages are immutable. Therefore, to change a property value, you must create and modify a new message. You create and modify the new message by inserting a message assignment shape between the Receive and Send shapes. First, however, you must reference the schema DLL to gain access to the TIBCO EMS properties.  
  
## Reference the schema DLL  
  
1.  In Visual Studio, open your BizTalk Server project, and open **Solution Explorer** .  
  
2.  Right-click **References**, and select **Add Reference**.  
  
     The **Add Reference** dialog box appears.  
  
3.  Click the **Browse** tab.  
  
     The **Select Component** dialog box appears.  
  
4.  Locate **\<TIBCO EMS_Adapter_installation_directory\>\bin**, and then select **Microsoft.Adapters.TibcoEMSProperties.dll**.  
  
5.  Click **Open**.  
  
     The DLL appears in the **Selected Components** in the **Add Reference** dialog box.  
  
6.  Click **OK** and then double-click your orchestration to access the Orchestration Designer.  
  
7.  On the **View** menu, point to **Other Windows**, and then click **Orchestration View**.  
  
8.  In the Orchestration view, right-click **Messages** and select **New Message**.  
  
9. Edit your new message properties and assign a **Message Type**.  
  
     You will assign Message_1 to Message_2. Therefore, you must assign the same message type to both messages.  
  
10. On the **View** menu, click **Toolbox**.  
  
11. Drag a **Message Assignment** shape onto your orchestration where you want to create a new message.  
  
12. Edit the outer ConstructMessage_1 shape and select your new message, Message_2, in the **Constructed Messages** property.  
  
13. Double-click the inner MessageAssignment_1 shape.  
  
     The BizTalk Expression Editor appears.  
  
14. In the BizTalk Expression Editor, type your code.  
  
15. First copy an existing message and then assign values to message context properties.  
  
     The syntax is `Message(property) = value;`. For example:  
  
    ```  
    Message_2 = Message_1;  
    Message_2( TibcoEMS.Priority) = 6;  
    ```  
  
     See TIBCO EMS for a list of supported properties that you can use in your custom message.  
  
16. Click **OK** to close the BizTalk Expression Editor and save your code.  
  
17. Click the Send shape and assign the **Message** to be **Message_2**.  
  
18. Verify that the shapes in the rest of the message flow operate on the appropriate message.  
  
19. Right-click your project in Solution Explorer, and select **Build**.  
  
20. Right-click your project and select **Deploy**.  
  
21. Select **Bind**, **Enlist**, and **Start** in the BizTalk Explorer to test your orchestration.  
  
## See Also  
[TIBCO EMS message context properties](../core/message-context-properties-in-biztalk-server.md)
