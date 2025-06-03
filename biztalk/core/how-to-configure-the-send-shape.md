---
description: "Learn more about: How to Configure the Send Shape"
title: "How to Configure the Send Shape"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Configure the Send Shape
![Image that represents the Send shape.](../core/media/ebiz-orch-send.gif "ebiz_orch_send")  
Send shape  
  
 If you expect to receive an indirect or asynchronous response (not using a request-response port) to the message that you have sent, you need to correlate the message with the currently running instance of the orchestration, so that the respondent can get the response to the correct instance. You can apply a following correlation set to the **Send** shape for a previously initialized correlation, or you can apply an initializing correlation set. For more information, see [Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md).  
  
### To configure a Send shape  
  
1.  Set a message and a port operation.  
  
    1.  In the Orchestration View window, verify that your orchestration has both a message and a port operation defined for the multi-part message type being sent.  
  
    2.  In the Properties window, select the message to send from the **Message** property drop-down list.  
  
    3.  In the Properties window, select the port operation that sends the message from the **Port Operation** drop-down list.  
  
         —Or—  
  
         Drag the send connector from the **Send** shape to the port socket that sends the message.  
  
2.  Specify correlation sets to restrict the messages the **Send** shape will send or to initialize the values in a correlation set.  
  
    1.  For each correlation set you want to use, check a correlation set from the drop-down on the **Following Correlation Sets** property.  
  
    2.  For each correlation set that you want to initialize, check a correlation set from the drop-down on the **Initializing Correlation Sets** property.  
  
## Delivery Notification  
 To test whether you have successfully sent a message over a send port, complete the following steps:  
  
1. Put your Send shape in a non-transactional, long-running or atomic scope.  
  
2. On your send port, set the DeliveryNotification property to **Transmitted**.  
  
3. Add a catch handler to your scope to handle a DeliveryFailureException.  
  
   > [!NOTE]
   >  If the Send shape is contained within an atomic scope, the DeliveryFailureException can still be caught, but will require an outer scope shape be added with a Transaction Type set to **Long Running** or **None**. Atomic scopes are not able to catch exceptions directly.  
  
   The orchestration waits for acknowledgment at the end of the enclosing non-atomic scope, or the end of the orchestration, to receive the acknowledgment.  
  
> [!NOTE]
>  This applies only to one-way operations; failure in two-way (request-response) operations results in a SoapException (negative acknowledgement) even without the port attribute being set.  
  
> [!NOTE]
>  Delivery notification is not supported for direct binding.  
  
## See Also  
 [Error Handling](../core/error-handling.md)
