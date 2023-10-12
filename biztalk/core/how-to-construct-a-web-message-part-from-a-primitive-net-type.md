---
description: "Learn more about: How to Construct a Web Message Part from a Primitive .NET Type"
title: "How to Construct a Web Message Part from a Primitive .NET Type"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Construct a Web Message Part from a Primitive .NET Type
You create a Web message part from a primitive .NET type by using a **Message Assignment** shape. Alternatively, you can create a Web message part from a primitive .NET type by using a .NET helper class to set the parts. For more information on creating message types by using a .NET class, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).  
  
### To construct a Web message part from a primitive .NET type  
  
1.  With an orchestration open, open the **Toolbox** and click the **BizTalk Orchestrations** tab.  
  
2.  Drag a **Construct Message** shape to the orchestration.  
  
3.  Edit the **Message Constructed** property to include the message instance that you created for the Web message type.  
  
4.  Drag a **Message Assignment** shape onto the **Construct Message** shape.  
  
5.  Double-click the **Message Assignment** shape to open the BizTalk Expression Editor.  
  
6.  Set the parts of the Web message type to their required values in the BizTalk Expression Editor box.  
  
     For example, the following code sets the expression to a string:  
  
    ```  
    ItemAvailRequestInstance.Item_ID = "This is Item_ID.";  
    ```  
  
## See Also  
 [Constructing Web Messages](../core/constructing-web-messages.md)
