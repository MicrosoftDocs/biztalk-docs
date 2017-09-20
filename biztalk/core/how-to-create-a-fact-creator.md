---
title: "How to Create a Fact Creator | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetFactTypes method"
  - "CreateFacts method"
  - "IFactCreator interface"
  - "Business Rules Framework, code samples"
  - "Business Rules Framework, fact creator"
  - "Business Rules Framework, programming"
ms.assetid: 0589be8e-34d6-4e55-b678-c1f8436d1f61
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
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