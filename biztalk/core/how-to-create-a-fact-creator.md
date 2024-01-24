---
description: "Learn more about: How to Create a Fact Creator"
title: "How to Create a Fact Creator"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Create a Fact Creator
You can write a fact creator to create instances of your facts. Your fact creator must implement **IFactCreator** and its **CreateFacts** method and **GetFactTypes** method. After you have created your fact creator dll, you can browse to it from within the policy tester. The following is an example of a fact creator implementation.  
  
```  
public class MyFactCreator : IFactCreator  
{  
   private object[] myFacts;  
   public MyFactCreator()  
   {  
   }  
   public object[] CreateFacts ( RuleSetInfo rulesetInfo )  
   {  
      myFacts = new object[1];  
      myFacts.SetValue(new MySampleBusinessObject(),0);  
      return myFacts;  
   }  
   public Type[] GetFactTypes (RuleSetInfo rulesetInfo)  
   {  
      return null;  
   }  
}  
```
