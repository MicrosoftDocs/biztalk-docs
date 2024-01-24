---
description: "Learn more about: Key Messages and Fields"
title: "Key Messages and Fields"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Key Messages and Fields
This section briefly describes key messages and fields handled by the **OrderBroker** and **OrderManager** orchestrations. For a complete list of messages in the application, see [Message Reference for the Business Process Management Solution](../core/message-reference-for-the-business-process-management-solution.md).  
  
## Order Messages  
 Order messages from the **OrderBroker** are multi-part messages. One part contains the routing information; the other part, the order information. The .NET class defining the routing message part makes all of its fields distinguished fields so that an orchestration can have access to all of the class members as message properties. The classes also include promoted fields in the routing class so that the messages are routable. All of the promoted fields are also distinguished fields so that they can be programmed against and referred to with less complex notation.  
  
 For more information about using .NET classes to define messages, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).  
  
## Identifying Orders  
 The solution uses three fields in the routing information to identify an order. Of these three, two identify the order: the order identifier (**OrderID**) and the customer identifier (**CustomerID**). However, although these two fields identify an order, there can be more than one instance of an order. For example, a customer might ordera a new standard cable installation and then call later to change the order to a new deluxe cable installation. It's unlikely that the original order will be finished before the updated order arrives. This creates two instances of the order.  
  
 To distinguish among instances of orders, the solution uses a unique order sequence number (**SeqNum**). The three fields **OrderID**, **CustomerID**, and **SeqNum** uniquely identify an instance of an order.  
  
 Finally, because the solution uses increasing numbers for the **SeqNum**, the solution can distinguish an update from the original order—the update has a higher **SeqNum**.  
  
> [!NOTE]
>  The solution relies on the systems creating order requests to assign ascending values to **SeqNum**. See the code behind the ASP page for the input web service, **CSRMainForm.aspx.cs**, and the map that converts the request to an order, **CSR_OrderRequest_To_Order.btm** for names of the fields involved.  
  
## Status  
 The **OrderBroker**, **OrderManager**, and their satellite orchestrations use two fields in the order message routing part to track state: **Status**, and **Stage**. The **Status** field tracks the status of the order. The following table describes the values for the **Status** field.  
  
|Value|Where Set|Description|  
|-----------|---------------|-----------------|  
|ACCEPTED|OrderBroker|Order can go on to OrderManager.|  
|COMPLETED|OrderManager|Processing of the entire order finished without error.|  
|ERROR|OrderManager|Error detected in order.|  
|ORDERMANAGER-EXCEPTION|OrderManager|Exception occurred in the order manager while processing the order.|  
|STAGE_n_COMPLETED|OrderManager|Indicates stage n, where n is a number, completed without error.|  
|STARTED|OrderManager|Order processing started.|  
|TERMINATED|OrderManager|Order processing stopped due to cancellation.|  
  
## Stage  
 The **OrderManager** uses the **Stage** field in the routing part to indicate the processing stage of a message. The field is used in filters that determine which satellite orchestration processes the message. The **OrderManager** initially sets **Stage** to one (1). When the order terminates or completes, the **OrderManager** sets **Stage** to the value of an orchestration variable, **Stop**.  
  
## RequestType  
 The **OrderManager** also uses the **RequestType** field of the order message. If the value of the field is TERMINATE, the order is to be terminated. The orchestration ignores all other values of the **RequestType** field and relies on the order sequence numbers to recognize order updates and duplicates. Otherwise, the **OrderBroker** sets the **RequestType** field to the value of the **Status** field in the message from the vendor or customer service system.  
  
## OrderTypeCode, OrderType, and ServiceClass  
 The type of the order is in the **OrderTypeCode** field of the order message. The **OrderBroker** sets its value to the value in the **OrdTypeCode** field in the message coming from either the customer service system or the vendor system. The following table shows the possible values for **OrderTypeCode**:  
  
|Value|Description|  
|-----------|-----------------|  
|NS|New standard cable installation.|  
|ND|New deluxe cable installation.|  
|XS|Cancel standard cable installation.|  
|XD|Cancel deluxe cable installation.|  
|CS|Change standard cable installation.|  
|CD|Change deluxe cable installation.|  
|UNKNOWN|Unknown.|  
  
 Later, the **Validate** orchestration uses the Business Rules Engine to translate these values into two separate fields, **OrderType** and **ServiceClass**. The **Validate** orchestration is called by the first order processing stage, **CableOrder1**.  
  
 The following table gives the values for the **OrderType**:  
  
|OrderTypeCode Values|OrderType Value|  
|--------------------------|---------------------|  
|NS, ND|ACTIVATE|  
|XS, XD|CANCEL|  
|CS, CD|CHANGE|  
|Invalid combination.|INVALID|  
  
 The values for **ServiceClass** are the corresponding single letter, **S** for standard, or **D** for deluxe.  
  
## Additional Identifiers  
 The solution also uses an identifier for each individual order. This identifier, **RequestId**, needs to be unique across all orders. The input web service automatically assigns a GUID to it. Messages submitted through the batch input must include a value for the field. The field is **RequestID** in the order schema. The **OrderBroker**, however, uses the **CSR_OrderRequest** schema to process orders. The field appears as **ReqId** in this schema and is a distinguished property.  
  
 The solution uses the **RequestId** to form the activity identifier used in the BAM tracking system.  
  
## See Also  
 [Process Manager Logic](../core/process-manager-logic.md)   
 [Order Flow through the Process Manager](../core/order-flow-through-the-process-manager.md)   
 [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md)   
 [Message Reference for the Business Process Management Solution](../core/message-reference-for-the-business-process-management-solution.md)
