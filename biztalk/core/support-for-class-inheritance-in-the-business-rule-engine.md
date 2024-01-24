---
description: "Learn more about: Support for Class Inheritance in the Business Rule Engine"
title: "Support for Class Inheritance in the Business Rule Engine"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Support for Class Inheritance in the Business Rule Engine
One of the key features of Object Oriented Programming (OOP) languages is inheritance. Inheritance is the ability to use all of the functionality of an existing class, and extend those capabilities without rewriting the original class.  
  
 The Business Rules Framework supports two types of class inheritance: implementation and interface. Implementation inheritance refers to the ability to use a base class's properties and methods with no additional coding. Interface inheritance refers to the ability to use just the names of the properties and methods, but the child class must provide the implementation.  
  
 The rules can be written in terms of a common base class, but the objects asserted into the engine can be from derived classes. In the following example, **RegularEmployee** and **ContractEmployee** are derived classes of the base class **Employee**.  
  
```  
class Employee  
   {  
      public string Status()  
      {   
         // member definition  
      }  
      public string TimeInMonths()        
      {   
         // member definition  
      }  
   }  
  
class ContractEmployee : Employee  
{  
   // class definition  
}  
class RegularEmployee : Employee  
{  
   // class definition  
}  
```  
  
 Assume you have the following rule.  
  
## Rule 1  
  
```  
IF Employee.TimeInMonths < 12  
THEN Employee.Status = "New"  
```  
  
 At run time, if the user asserts two objects, one an instance of **ContractEmployee** and the other an instance of **RegularEmployee**, both the object instances are evaluated against the rule described earlier.  
  
 The user can also assert derived class objects in actions by using an **Assert**. This causes the rules that contain the derived object and its base type in their conditions to be re-evaluated, as shown in the following example.  
  
## Rule 2  
  
```  
IF Employee.Status = "Contract"   
THEN Employee.Bonus = false  
Assert(new ContractEmployee())  
```  
  
 All rules containing the **Employee** type or the **ContractEmployee** type in their conditions get re-evaluated after the assertion. The type of inheritance in this example is implementation. Even though only the derived class is asserted, the base class also gets asserted if rules are written using methods in the base instead of the derived class.  
  
## See Also  
 [Rule Engine](../core/rule-engine.md)
