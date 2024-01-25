---
description: "Learn more about: Appending Nodes to Messages in User Code"
title: "Appending Nodes to Messages in User Code"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Appending Nodes to Messages in User Code
Because of the way BizTalk Server handles messages, you cannot simply append a new node directly to an existing message. Instead, you must clone the existing message, as follows:  
  
```  
myXMLDoc = myExistingMsg; // just holding a reference  
// use CloneNode to make a fresh copy of myModifiedMsg  
myXMLDoc = (XMLDocument)myXMLDoc.CloneNode;  
myXMLDoc.append myNode; // here is the node we want to append  
//update temp message   
myModifiedMsg = myXMLDoc;  
```  
  
 Now you can use myModifiedMsg, which includes the new node. If for some reason you want to reuse myExistingMsg, you can construct a new (empty) copy and assign myModifiedMsg to it.  
  
```  
myExistingMsg = myModifiedMsg;  
```  
  
## See Also  
 [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md)   
 [Constructing Messages](../core/constructing-messages.md)
