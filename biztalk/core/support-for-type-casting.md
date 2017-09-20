---
title: "Support for Type Casting | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6af46e34-5e33-4f61-8c19-4348f1bb4d4a
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Support for Type Casting
You can use the **Cast** method of the **ClassMemberBinding** class to convert an object of one type to an object of another compatible type. Currently, the Business Rule Composer tool does not support creating rules by using the **Cast** method. You must create the rules programmatically by using the rule engine object model to take advantage of this feature.  
  
 The following sample code demonstrates how to use the **Cast** method to convert an instance of the **System.Object** class to an instance of the **Cls2** class. This sample also demonstrates how to access a nested member of a class as described in [Accessing Nested Members of a Class](../core/accessing-nested-members-of-a-class.md).  
  
```  
using Microsoft.RuleEngine;  
  
namespace RuleTypeCasting  
{  
    class Cls1  
    {  
        //Note that return type is 'object', not Cls2  
        public object GetCls2Obj()  
        {  
            return new Cls2();  
        }  
    }  
  
    class Cls2  
    {  
        public void Log()  
        {  
            Console.WriteLine("In Cls2.Log method");  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            //Create the condition list IF 1 == 1  
            Equal eq = new Equal(new Constant(1), new Constant(1));  
  
            //Create the action collection  
            ActionCollection ac = new ActionCollection();  
  
            //Create the class binding for the Cls1 class  
            ClassBinding cbCls1 = new ClassBinding(typeof(Cls1));  
  
            //Create the class member binding for the GetCls2Obj method in the Cls1 class  
            ClassMemberBinding cmGetCls2Obj = new ClassMemberBinding("GetCls2Obj", cbCls1);  
  
            //Type casting the return value of GetCls2Obj method (object) to Cls2 type  
            cmGetCls2Obj.Cast(typeof(Cls2));  
  
            //Create the class member binding to the Log method of Cls2 type   
            ClassMemberBinding cmLog = new ClassMemberBinding("Log", cmGetCls2Obj);  
  
            //Create a user function based on cmLog and add it to the action collection  
            UserFunction ufLog = new UserFunction(cmLog);  
            ac.Add(ufLog);  
  
            // Create the rule  
            Rule rl = new Rule("InvokeLogRule", eq, ac);  
  
            // Create the rule set or policy  
            RuleSet rs = new RuleSet("InvokeLogPolicy");  
            rs.Rules.Add(rl);  
  
            //Create the facts  
            Cls1 Cls1Obj = new Cls1();  
  
            //Execute the policy  
            PolicyTester tester = new PolicyTester(rs);  
            tester.Execute(Cls1Obj);  
  
        }  
    }  
}  
```  
  
## See Also  
 [Support for Class Inheritance in the Business Rule Engine](../core/support-for-class-inheritance-in-the-business-rule-engine.md)   
 [Accessing Nested Members of a Class](../core/accessing-nested-members-of-a-class.md)