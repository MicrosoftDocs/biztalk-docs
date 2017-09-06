---
title: "GetEndpointName | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5a06850-ff6d-4fe4-9834-61d14b117391
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# GetEndpointName
Pushes the name of the current interception endpoint onto the stack.  
  
## Syntax  
  
```  
  
<wcf:Operation Name="GetEndpointName" />  
```  
  
#### Parameters  
 None.  
  
## Pushed Value  
 String containing the current interception endpoint name.  
  
## Remarks  
 It is important to note that the client and server applications will return different names for the same endpoint name specified in the App.config files.  
  
 For client applications, the endpoint name retrieved by the GetEndPointName operation is the binding name followed by an underscore and the contract name.  
  
 For example, if the Name property on ServiceEndpoint is not set but the binding is set, the name will be set to \<*binding*>_\<*contract*>.  
  
 If the name and binding are not set, the Name property will be set to \<*contract*>.  
  
 For the service, the name retrieved is the endpoint name specified in the App.config file.  
  
## Example  
 The following example filter expression defines an interception for the Receive operation for the ServiceRequest contract call point for the PurchaseOrder_EP endpoint. This is done in the following logical steps:  
  
1.  Compare the current operation name to "Receive" and push the result (true or false) onto the stack.  
  
2.  Compare the current service contract call point to "ServiceRequest" and push the result (true or false) onto the stack. There are now two Boolean values on the stack.  
  
3.  Compare the results of the preceding steps using a Boolean **And** operation and push the result on the stack. This leaves one Boolean value on the stack.  
  
4.  Compare the current endpoint to "PurchaseOrder_EP" and push the result (true or false) onto the stack. There are now two Boolean values on the stack.  
  
5.  Finally, compare the two Boolean values on the stack using a Boolean **And** operation and push the result onto the stack. This checks the result of the endpoint comparison against a Boolean value, which is true if the operation name and contract call point successfully matched, and which is false otherwise.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wcf:Operation Name="GetOperationName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Receive</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wcf:Operation Name="GetServiceContractCallPoint" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ServiceRequest</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wcf:Operation Name="GetEndpointName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>PurchaseOrder_EP</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## See Also  
 [Operations in Windows Communication Foundation](../core/operations-in-windows-communication-foundation.md)