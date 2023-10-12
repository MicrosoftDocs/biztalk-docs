---
description: "Learn more about: Message References in Message Assignment Shape"
title: "Message References in Message Assignment Shape"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Message References in Message Assignment Shape
When you first assign a .NET-based object to a message or message part, that message holds and maintains a reference to the object.  
  
 For efficiency and scalability, the orchestration engine does not do a "deep copy" of the object: that is, it does not copy the entire contents of the object to the message.  
  
 If you subsequently assign the object to another message or message part, any modifications to the original results in modifications to the second message or message part. You should avoid this practice, because results are unpredictable.  
  
 If you need your second message to have a distinct copy of the object, you should assign the first message or message part to the second message or message part.  
  
 Consider the following example:  
  
 Wrong way:  
  
```  
myMsg1 = myObj; // assign the first message  
myMsg2 = myObj; // assign the second message (wrong!)  
myMsg2.myInt = 100; // modify the second  
myMsg1.myInt = 5;  
```  
  
 In this case, myMsg2.myInt has been overwritten, and now has the value 5.  
  
 Right way:  
  
```  
myMsg1 = myObj; // assign the first message  
myMsg2 = myMsg1; // assign the second message (right!)  
myMsg2.myInt = 100; // modify the second  
myMsg1.myInt = 5;  
```  
  
 In this case, myMsg2.myInt still has the value 100, as expected.  
  
## See Also  
 [Constructing Messages](../core/constructing-messages.md)
