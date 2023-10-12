---
description: "Learn more about: Dynamic Adapter DisplayUI Method"
title: "Dynamic Adapter DisplayUI Method"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Dynamic Adapter DisplayUI Method
This method on the **IDynamicAdapterConfig** interface displays the custom user interface for the custom adapter. This enables the user to view, select, and import the related supporting files based upon the selected services into their BizTalk project.  
  
 In the file adapter, modify the code within the **displayUI** method of the AdapterManagement.cs file to create a custom user interface (UI) for selecting the type of schema to accept. After a schema is selected, choose the appropriate WSDL file.  
  
 The following code is from the **displayUI** method of the AdapterManagement.cs file.  
  
```  
/// <summary>  
        /// Acquire wsdl(s) from which to build the user interface  
        /// </summary>  
        /// <param name="endPointConfiguration"></param>  
        /// <param name="owner"></param>  
        /// <param name="WSDLList">Array of custom UI's WSDL (returned)</param>  
        /// <returns></returns>  
        public Result DisplayUI(IPropertyBag endPointConfiguration,   
            IWin32Window owner,  
            out string [] WSDLList)   
      {  
            WSDLList = new string[1];  
            WSDLList[0] = GetResource("AdapterManagement.service1.wsdl");  
            return Result.Continue;  
        }  
```
