---
description: "Learn more about: GetOperationName"
title: "GetOperationName"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# GetOperationName
Pushes the name of the current operation onto the stack.  
  
## Syntax  
  
```  
  
<wcf:Operation Name="GetOperationName" />  
```  
  
#### Parameters  
 None.  
  
## Pushed Value  
 String containing the name of the current operation.  
  
## Remarks  
 When using GetOperationName, make sure you compare the operation name as it is invoked by your application. For example, if you use the name attribute on a service contract to assign a custom name, the client will have its default proxy generated with the custom name for the method. However, the server application will use the actual method names for the corresponding operations and not the one specified in the name attribute.  
  
## Example  
 In the following sample, `GetOperationName` is used to build an expression that filters for the operation named "AuthorizePayment".  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wcf:Operation Name="GetOperationName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>AuthorizePayment</ic:Argument>  
    </ic:Operation>  
  </ic:Expression>  
</ic:Filter>  
```  
  
## See Also  
 [Operations in Windows Communication Foundation](../core/operations-in-windows-communication-foundation.md)
