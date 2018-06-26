---
title: "How to Use Optional Explicit-Level Override Authentication1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c58f3a9d-865c-4011-be71-ef31481b94fe
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Use Optional Explicit-Level Override Authentication
Clicking the **Allow application override** check box enables applications to supply credentials at run time through a callback mechanism supplied by Transaction Integrator (TI). Using application override does not require the installation and use of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Enterprise Single Sign-On (ESSO). Instead, the client application supplies TI with a pointer to a callback object that can be used to request credentials when they are needed at run time. A utility component is provided so that customers can add their callback pointer to the context, and create new COM+ objects that inherit from the modified context. The security callback component is automatically installed.  
  
> [!NOTE]
>  Explicit-Level Override Authentication is not the preferred method of specifying credentials for a client. If possible, you should use the Client Context USERID and PASSWORD override keywords. For more information, see the [COMTIContext Keywords](./comticontext-keywords1.md).  
  
 To use explicit security, the client application must follow these steps:  
  
### To use explicit security  
  
1. Create an instance of an object that implements `IHostSecurityCallback`.  
  
    This object is created in the client application and is implemented by the developer.  
  
2. Create an instance of the TI utility object `COMTI.HostSecurityContext`.  
  
3. Call `SetCallbackObject` on the utility object, and pass it the `IHostSecurityCallback` pointer on the callback object.  
  
4. Create instances of its TI component by using the `CreateInstance` method on the security utility object.  
  
   When the TI component instance created in step 4 establishes a conversation with the host, it calls the `ReturnSecurityInfo` method on the callback object. TI passes this method the name of the remote environment being contacted. The output parameters provide the logon and password as clear text.  
  
   As an additional aid to developers, TI provides the type information for the `IHostSecurityCallback` interface inside the component library for the TI security component. This enables Visual Basic developers to set a reference to this component and then use the `Implements` keyword to implement the callback class.  
  
## See Also  
 [Security Implications](../core/security-implications1.md)