---
description: "Learn more about: How to Program with Discriminated Unions"
title: "How to Program with Discriminated Unions2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Program with Discriminated Unions
A discriminated union is a data structure that can hold a data value of several different types. Host Integration Server uses discriminated unions with several providers, such as the Managed Provider for Host Files. When creating an application that uses Remoting or Web Services, you must satisfy the Web Services Description Language (WSDL) requirements for the discriminated union. WSDL generation constraints require that all structures in an object be used in a method call. Therefore, you need to ensure that all the structures in a discriminated union are also used, even if only in a piece of stub code.  
  
### To use a discriminated union with Remoting or Web Services  
  
1.  Create your schema as normal.  
  
2.  Identify any structure in the discriminated union that is not explicitly used in another method call.  
  
3.  Create a dummy method call that calls the unused structure.  
  
## Example  
 The following example shows a line of dummy method that uses several discriminated union structures. By having such a method, the WSDL generation requirements are satisfied.  
  
```  
void dummyroutine1 (ACCT_TYPE_SAVE acct_type_sav, ACCT_TYPE_CHK acct_type_chk)  
```  
  
## See Also  
 [Programming Windows-Initiated Processing](../core/programming-windows-initiated-processing1.md)
