---
title: "Component Interface User-Defined Methods | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "component interfaces, user-defined methods"
  - "user-defined methods, component interface"
  - "custom component interfaces, limitations"
  - "collection limitations"
  - "custom methods, samples"
  - "samples, custom methods"
  - "component interfaces, limitations for custom CI"
ms.assetid: e4b15889-35ff-44aa-819d-eade9690bdd6
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Component Interface User-Defined Methods
Microsoft BizTalk Adapter for PeopleSoft Enterprise supports user-defined methods in component interfaces. The signatures are of the form:  
  
```  
myRet=myCI.myMethod(parameter1, parameter2, ...)  
```  
  
 where:  
  
- `parameter1`, `parameter2` are input parameters.  
  
- `myRet` is the return value.  
  
  The parameters can only be input parameters to the method. Only one value can be returned from the method as the return parameter.  
  
> [!NOTE]
>  The component interface that contains user-defined methods should only have the PeopleSoft `Get` function enabled. If the component interface has keys, then custom methods will not work.  
  
## Custom CI Limitation  
 BizTalk Adapter for PeopleSoft Enterprise can handle custom PeopleSoft methods provided that the component interface does not have keys. If the component interface has keys, custom methods will not work.  
  
### Workaround  
 Create a new component interface that does not have keys, and write a new custom method that incorporates the keys as part of the calling parameters. For example, you could use the SetPassword custom method in the USER_PROFILE component interface; however USER_PROFILE has keys. You can create a new component interface that has no keys, and then create a custom method in your new component interface. This method would accept two parameters, user ID and password. The custom method could then invoke USER_PROFILE with a `Get` and then invoke `SetPassword`. Consult the PeopleSoft documentation for more details.  
  
 Due to a limitation in PeopleSoft, `Date`, `DateTime`, and `Time` types appearing in user-defined methods are mapped as strings in the client code.  
  
## Collection Limitation  
 User-defined methods cannot return a collection, or more generally, any API object. This means that you can only return simple types, for example, strings and numbers. You can get around this limitation by sending a collection as an XML string and programming the client to parse the strings to extract the items into the correct format. You can examine the GET_CI_INFO custom component interface to see an example of this workaround.  
  
## Sample Custom Method  
 You can use the following basic custom method, SayHello, to test the functionality of your component interface using custom methods.  
  
 The following PeopleCode function is a user-defined method of a PeopleSoft component interface named ACB_EMPLOYEE. The sample returns a string where the return value is **Hello** followed by the value of the input parameter.  
  
```  
Function SayHello(&sName As string) Returns string  
      &EOL = Char(10);  
      &sResult = "Hello " | &sName | &EOL;  
      Return &sResult;  
End-Function;  
```  
  
> [!NOTE]
>  To modify multiple tables at the same time (using one command) you can either create another component interface or create a component interface user-defined method.  
  
## See Also  
 [Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md)