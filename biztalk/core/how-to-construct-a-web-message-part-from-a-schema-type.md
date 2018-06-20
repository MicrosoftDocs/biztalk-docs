---
title: "How to Construct a Web Message Part from a Schema Type | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, Web messages"
  - "Web messages, schema types"
  - "Web messages, creating"
  - "Transform shape [Orchestration Designer]"
  - "Web messages, Transform shape [Orchestration Designer]"
ms.assetid: 4452ade6-b10f-4564-bffc-18114896aeeb
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Construct a Web Message Part from a Schema Type
You create a Web message part from a schema type by using a **Transform** shape. Alternatively, you can create a Web message part from a schema type by using a .NET helper class to set the parts. For more information on creating message types by using a .NET class, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).  
  
### To construct a Web message part from a schema type  
  
1. Add a new map. For information about creating maps, see [How to Create New Maps](../core/how-to-create-new-maps.md).  
  
2. In BizTalk Mapper, click **Open Destination Schema** in the **Destination Schema** pane of the map and in the **BizTalk Type Picker** dialog box, expand the **Schemas** node, select the schema for the added Web reference, and then click **OK**.  
  
   > [!NOTE]
   >  The format of the Web reference schema is **\<project default namespace\>.\<Web reference name\>.Reference**.  
  
3. In the **Root Node for Target Schema** dialog box, select a root node for the destination schema, and then click **OK**. For more information about how to determine a root node for a Web message part type, see [How to Determine a Web Message Part Type](../core/how-to-determine-a-web-message-part-type.md).  
  
4. Click **Open Source Schema** in the **Source Schema** pane of the map and in the **BizTalk Type Picker** dialog box, expand the **Schemas** node, select the source schema to map data from, and then click **OK**.  
  
5. In the BizTalk Mapper, create links between the source schema and target schema.  
  
6. Open an existing orchestration (or create a new orchestration), open the **Toolbox**, and click the **BizTalk Orchestrations** tab.  
  
7. Drag a **Construct Message** shape to the orchestration.  
  
8. Edit the **Message Constructed** property to include the message instance that yo created for the Web message type.  
  
9. Drag a **Transform** shape onto the **Construct Message** shape and double-click to open the **Transform Configuration** dialog box.  
  
10. Click the **Existing Map** button and select the map that you created in step one in the **Fully Qualified Map Name** list box.  
  
11. In the **Transform** pane, select **Source**. In the **Source Transform** pane, select a valid message instance from the list box.  
  
12. In the **Transform** pane, select **Destination**. In the **Destination Transform** pane, select the Web message instance from the list box, and then click **OK**.  
  
    For more information about using the **Transform Configuration** dialog box, see [How to Configure the Transform Shape](../core/how-to-configure-the-transform-shape.md).  
  
    You can also use this procedure to map the Web method response message instance to another Web message instance.  
  
## See Also  
 [Constructing Web Messages](../core/constructing-web-messages.md)