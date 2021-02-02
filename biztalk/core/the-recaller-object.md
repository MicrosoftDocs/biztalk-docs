---
description: "Learn more about: The Recaller Object"
title: "The Recaller Object | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Recaller object"
  - "Invoke method"
  - "process management solution tutorial, Recaller object"
  - "process management solution tutorial, errors"
ms.assetid: b30ad1ae-475f-4913-b402-4d3263fcf072
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The Recaller Object
The business process management solution provides for retrying, in a generic way, some failed object method calls. The solution does this through the **Recaller** object in the **ExceptionHandler** orchestration. The **ExceptionHandler** orchestration uses the object to retry object method calls. For more information, see [The ExceptionHandler Orchestration](../core/the-exceptionhandler-orchestration.md).  
  
## The Invoke Method  
 The **Recaller** object has a single, static method, **Invoke**. Because it is static, you never need to create an instance of the **Recaller** object. You can use the **Invoke** method in three ways: to construct an object, to call a static method for an object, or to call a non-static method for an object.  
  
> [!NOTE]
>  The **Invoke** method serves as a wrapper for the **Type.InvokeMember** method in the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Class Library.  
  
### Arguments for the Invoke Method  
 The following table describes arguments for the **Invoke** method:  
  
|Parameter|Type|Description|  
|---------------|----------|-----------------|  
|*t*|**Type**|The type of the object on which to call the method.|  
|*obj*|**Object**|The instance of the object to use.|  
|*methodName*|**string**|The name of the method to invoke.|  
|*args*|**Array**|An array of type **Object** containing the method's arguments.|  
  
 To call the constructor for an object, use an empty string ("") or **null** for *methodName*.  
  
 To call a static method, use **null** for *obj*.  
  
 To call a non-static method, supply all of the arguments.  
  
> [!NOTE]
>  Using **null** as the value of the Type argument, *t*, causes **Invoke** to throw an **ArgumentNullException** exception. The argument *t* should not be null because the **Invoke** method uses the **Type.InvokeMember** [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] method.  
  
## Calling Invoke  
 In the solution, only the **ExceptionHandler** orchestration uses the **Recaller** object. The **ExceptionHandler** is, in turn, used by other orchestrations. The values passed to the **Invoke** method come from these other orchestrations. For example, the following code appears in the **Activate** orchestration in the **InitialException** Expression shape:  
  
```  
Ex = CodeEx;  
ObjectType = orderHandler.GetType();  
CalledObject = orderHandler;  
Reason = "Standard Activate Failed";  
MethodName = "Activate";  
ParameterArray = System.Array.CreateInstance(typeof(System.Object),  
                                              3 );  
ParameterArray.SetValue(ServiceType, 0);  
ParameterArray.SetValue(OrderMsg.CustNum, 1);  
ParameterArray.SetValue(OrderMsg.OrderNum, 2);  
ReturnValue = null; // no return value expected  
  
```  
  
 Notice how the code creates an array using **System.Array.CreateInstance** and uses the **SetValue** method to store the values used in it.  
  
 After the Expression shape, the Activate orchestration calls the **ExceptionHandler** orchestration. The following code shows how the orchestration designer translates the Call shape:  
  
```  
call Microsoft.Samples.  
    BizTalk.SouthridgeVideo.  
        OrderManager.ExceptionHandlerOrch  
            (  
                Reason,  
                Ex,  
                CalledObject,  
                MethodName,   
                ParameterArray,   
                OrderCorrelation,   
                OrderMsg,   
                out ReturnValue,   
                ObjectType  
            );  
  
```  
  
 In the **ExceptionHandler** orchestration, the following code appears in the **Call Original Code** Expression shape:  
  
```  
ReturnValue =   
    Microsoft.Samples.  
        BizTalk.SouthridgeVideo.  
            Utilities.Recaller.  
                Invoke(  
                    ObjectType,  
                    CalledObject,  
                    MethodName,  
                    ParameterArray  
                );  
```  
  
 Notice that, although the argument names match those in the Activate orchestration's call, arguments are matched by order and not by name when calling orchestrations.  
  
## See Also  
 [Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [The ExceptionHandler Orchestration](../core/the-exceptionhandler-orchestration.md)
