---
description: "Learn more about: How to Copy Data to the Message Context as Distinguished Fields"
title: "How to Copy Data to the Message Context as Distinguished Fields | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 004a13ca-a162-4a5e-9f72-8a5c55bbb7a6
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Copy Data to the Message Context as Distinguished Fields
This topic provides step-by-step instructions for promoting a property as a **Distinguished Field**.  
  
 You might choose **Distinguished Field** promotion over **Property Field** promotion for the following reasons:  
  
-   **Property Field** values are limited to 255 characters in length.  
  
-   **Property Field** values are stored in a database, and therefore have more overhead than **Distinguished Fields**. **Distinguished Fields** do not require any additional storage; they are essentially an alias for an **XPath**, thereby allowing orchestrations to more easily access the relevant values directly from the message.  
  
### To promote a property as a Distinguished Field  
  
1.  In BizTalk Editor, open the schema for which you want to promote one or more properties, and then select the (first) **Field Element**, **Field Attribute**, or **Record** node that you want to promote as a **Distinguished Field**.  
  
    > [!NOTE]
    >  Record nodes can never be promoted as **Distinguished Fields**, regardless of the type of content they contain.  
  
2.  Right-click the selected node, click **Promote**, and then click **Show Promotions**.  
  
     The **Promote Properties** dialog box opens with the selected node showing as selected in the schema tree on the left side of the dialog box.  
  
3.  In the **Promote Properties** dialog box, select the **Distinguished Fields** tab.  
  
4.  With the node to be promoted still selected in the schema tree on the left side of the **Promote Properties** dialog box, click **Add**.  
  
     If allowed, the selected node is added to the list on the **Distinguished Fields** tab. If not allowed, a message box provides an explanation.  
  
5.  You can select additional nodes for promotion in the schema tree on the left side of the dialog box, clicking **Add** after each selection.  
  
6.  When complete, click **OK**.  
  
     The nodes that you selected to promote are now **Distinguished Fields**.  
  
## See Also  
 [Promoting Properties](../core/promoting-properties.md)   
 [How to Create Property Schemas](../core/how-to-create-property-schemas.md)   
 [Ways to Use Message Content to Control Message Processing](../core/ways-to-use-message-content-to-control-message-processing.md)
