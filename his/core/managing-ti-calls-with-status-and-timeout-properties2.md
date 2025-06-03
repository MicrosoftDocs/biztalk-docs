---
description: "Learn more about: Managing TI Calls with Status and Timeout Properties"
title: "Managing TI Calls with Status and Timeout Properties2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Managing TI Calls with Status and Timeout Properties
A client application can manage its calls to a Transaction Integrator (TI) Automation server by checking the TI component's remote environment (RE) **Status** property and the **Timeout** property.  
  
## Status Property  
 TI provides a read-only RE **Status** property in each component library created by Host Integration Server Designer (HIS Designer). A client application can use this property to inquire about the current state of the RE with which a TI component is associated. It returns whether the RE is enabled, disabled, or blocked by a communications difficulty.  
  
## Timeout Property  
 All RE types supported by TI include a **Timeout** property. Set the **Timeout** property value on the **LU 6.2** or **TCP/IP** tab of the remote environment's properties page in TI Manager.  
  
 By default, an RE has no initial **Timeout** property value. Therefore, unless you use TI Manager to set a **Timeout** value, the TI run-time environment waits indefinitely for the mainframe transaction program (TP) to return output parameters. Meanwhile, the TI run-time environment blocks the calling client application until this response is received. This blocking behavior is typical for APPC applications.  
  
 For example, with LU 6.2, if an IMS program is disabled, request messages continue to be placed successfully on the IMS message queue without network errors being reported. This occurs even when these messages are not being processed.  
  
 Set the **Timeout** value to free a blocked client application after the time-out interval expires. After the time-out period expires, the client application is notified that a time-out error occurred when attempting to execute the IMS program. However, because the requests are successfully stored in the IMS message queue, the requests can still be processed later if the IMS program is enabled without first emptying the IMS queue.  
  
 Use TI Manager to specify a **Timeout** value, in seconds, for a given remote environment. Right-click the RE, and then click **Properties**.  
  
### Handling Time-out Errors  
 When sending messages to the CICS or IMS region described by a specific RE, the TI run-time environment measures the amount of elapsed time that occurs from when a request is sent to when a response is received. If the time-out interval elapses before receiving a response, the TI Automation server object is terminated, and the associated COM+ transaction stops the transaction and reports the error to the client application. A message describing this error is also written to the Windows Event Log.  
  
 To handle a time-out error, the TI run-time environment unbinds the LU 6.2 session established with the CICS or IMS region. This means that the TI run-time environment must reestablish a new LU 6.2 session before another message can be sent to this region. If the time-out error occurs over a TCP/IP connection, TI shuts down the TCP/IP connection.  
  
 Time-out errors can adversely affect the performance of TI. Therefore, you should set time-out values high enough to signal a significant failure in the remote CICS or IMS region.  
  
> [!NOTE]
>  For TCP/IP, the time-out value set on an RE's properties page is significant only to the sending and receiving of data. In contrast, the time-out value for establishing the connection itself is defined by the implementation of the underlying TCP transport.  
  
## See Also  
 [Creating and Managing TI Components](../core/creating-and-managing-ti-components2.md)   
 [Transaction Integrator User's Guide](../core/transaction-integrator-user-s-guide2.md)
