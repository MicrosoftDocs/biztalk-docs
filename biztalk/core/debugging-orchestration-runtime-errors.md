---
description: "Learn more about: Debugging Orchestration Runtime Errors"
title: "Debugging Orchestration Runtime Errors"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Debugging Orchestration Runtime Errors
This section contains a set of questions and answers designed to help you resolve runtime issues with your orchestrations.  
  
## Why do I get intermittent subscription errors when sending to a child orchestration that was just started by the parent?  
 The subscription error "could not find subscription" is a result of a race condition. A race condition occurs when the outcome of a process depends on the particular order in which the process takes place. In this case, the condition occurs when the child orchestration has not been started in time to receive the message sent by the parent.  
  
 To avoid this problem, the child orchestration could send a message back to the parent when it has been started and is prepared to receive a message. In this way, the parent orchestration that started it would know that there is a receiver before sending a message.  
  
## Why do I get errors when I attach a dynamic send port to a logical port?  
 A dynamic port is not designed to inherit all of the attributes and characteristics of the port assigned to it. A dynamic port gets an address only; it does not inherit the other information associated with the logical port.  
  
 For example, if you attach a dynamic send port to a logical port with Delivery Notification = Transmitted, the runtime will not deliver a delivery notification. The XLANGs runtime only listens for a delivery notification if the port has actually been set up that way statically.  
  
> [!NOTE]
>  In XLANGs, ports will behave only as they have been configured statically.  
  
## When I try to run my application after deploying an orchestration with custom components, why do I get the error "File or Assembly name or one of its dependencies not found"?  
 This error usually means the BizTalk orchestration engine cannot locate the custom component. You must install all assemblies included in a BizTalk application in the global assembly cache of the computer that hosts the application.  
  
## An "AssemblyName context property was not valid" error occurs when submitting a document to a Web service via an orchestration  
  
### Problem  
 Submitting a document to a Web service via an orchestration results in an "AssemblyName context property not valid" error.  
  
### Cause  
 The BizTalk application was originally designed using a "messaging" approach without an intervening orchestration. This type of solution uses a send port filter to link the receive port and the send port so that the document is passed through to the send port upon receipt. Later, the solution was modified to include an orchestration that was bound to the send port.  
  
### Resolution  
 Remove the filter on the send port. If you apply a filter to a send port that is bound to an orchestration, messages will often bypass the orchestration and cause the context property error.  
  
## A "WrongBodyPartException" occurs when handling a multipart MIME message in an orchestration  
  
### Problem  
 Receiving a multipart MIME message into an orchestration results in a **WrongBodyPartException** exception.  
  
### Cause  
 This error can occur if the order of the parts is specified incorrectly or messages do not conform to the part positions you have specified. For example, if you specify that the third part is a body part but messages arrive with a header part in the third position.  
  
### Resolution  
 Verify that the body part index setting is correct and then ensure that all messages arriving through the adapter are consistent with the setting. You can inspect the contents of MIME messages that fail inside an orchestration by stopping the orchestration (but keeping it enlisted); this will force the message to be published so you can examine it using the Administration console and verify the order of the parts.  
  
## Multipart MIME message part cannot be found  
  
### Problem  
 Attempts to retrieve a MIME message part with an index value greater than 0 results in the BizTalk Server runtime throwing an error similar to "can't find multi-part message with index = \<value\>".  
  
### Cause  
 The most common causes for this error are:  
  
-   The MIME message has fewer parts than expected.  
  
-   The MIME message could not be fully parsed.  
  
### Resolution  
 You can resolve this problem by ensuring that your code retrieves only message parts that are within the range expected from the message source. In the case of a parsing issue, you should verify that the original MIME message is structurally sound and properly constructed. If you expect occasional parsing problems, ensure that your orchestration has appropriate exception handlers.  
  
## You receive a "The FILE send adapter cannot open file for writing" error when sending using a dynamic send port  
  
### Problem  
 You receive a "The FILE send adapter cannot open file *\<filename\>* for writing" error in the BizTalk Server event log when sending using a dynamic send port.  
  
 This problem occurs when the **BTS.OutBoundTransportLocation** property is defined in an orchestration expression and the file transport is specified, for example the following expressions will cause this error at runtime:  
  
```  
Message2=Message1;  
Message2(BTS.OutboundTransportLocation) = "file:///c:/test/out";  
MySendPort(Microsoft.XLANGs.BaseTypes.Address)=Message2(BTS.OutboundTransportLocation);  
```  
  
 \- Or -  
  
```  
Message2=Message1;  
Message2(BTS.OutboundTransportLocation) = "file://mymachine/test/out";  
MySendPort(Microsoft.XLANGs.BaseTypes.Address)=Message2(BTS.OutboundTransportLocation);  
```  
  
### Cause  
 This problem occurs because at runtime the orchestration engine removes the text "**file://"** from the specified URL. So, using the examples above, "file:///c:/test/out" is evaluated as \c:\test\out and "file://mymachine/test/out" is evaluated as mymachine\test\out.  
  
### Resolution  
 When specifying the URL for the **BTS.OutBoundTransportLocation** property in an expression, add or remove "/" characters as needed. Using the examples above the **BTS.OutBoundTransportLocation** property should be defined as "file://c:/test/out", which would evaluate to c:\test\out or "file:////mymachine/test/out", which would evaluate to \\\mymachine\test\out.
