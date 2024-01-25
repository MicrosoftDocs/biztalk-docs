---
description: "Learn more about: Messages Represented as .NET Classes"
title: "Messages Represented as .NET Classes"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Messages Represented as .NET Classes
This approach first involves creating a .NET class that defines your message type. The class must have a default constructor or the orchestration using it will not compile. A simple example of such a class is shown here.  
  
```  
using System;  
using Microsoft.XLANGs.BaseTypes;  
Using PropertyNamespace;  
  
namespace NetClass  
{  
   [Serializable]  
   public class MsgClass  
   {  
      public MsgClass()  
      {  
         StrField = "OK";  
         IntField = 1;  
         ShortField = 1;  
      }  
  
      [PropertyNamespace.ShortPropertyName]  
      public Int16 ShortField;  
  
      [PropertyAttribute(typeof(PropertyNamespace.StringPropertyName)]  
      [DistinguishedFieldAttribute()]  
      public String StrField;  
  
      [DistinguishedFieldAttribute()]  
      public int IntField;  
   }  
}  
```  
  
 In the above example, ShortField would be a property of type PropertyNamespace.ShortPropertyName and the underlying type of the property would have to be Int16 which is the type of ShortField. StrField would be both a distinguished field and a property of type PropertyNamespace.StringPropertyName and the underlying type of the property would have to be type of String which is the type of StrField. Normally both PropertyNamespace.StringPropertyName and PropertyNamespace.ShortPropertyName would be created through the BizTalk Schema Editor as schema properties, and you need to reference the assembly which contains the schema properties in your C# project.  
  
> [!NOTE]
>  In C# programming language, the Attribute ending of an attribute name is optional, so you can omit the Attribute ending and use DistinguishedField or Property instead. For example,  
  
```  
[Property(typeof(PropertyNamespace.StringPropertyName))]  
[DistinguishedField]  
public string StrField;  
```  
  
 Once the message type is defined, it is very easy to write code in the orchestration that will create a new message of this type. Within a **Construct Message** shape, you write simple expressions to create a new message of the **MsgClass** type shown above, and then assign values to the fields which are attributed as Distinguished Fields (if you wish to override the default values). Note that MyMsg is an orchestration message variable whose type is NetClass.MsgClass.  
  
```  
MyMsg = new NetClass.MsgClass();  
MyMsg.StrField = "Changed Value";  
MyMsg.IntField = 15;  
```  
  
## See Also  
 [Messages Represented as XSD Schemas](../core/messages-represented-as-xsd-schemas.md)   
 [Messages Represented as XLANGMessage](../core/messages-represented-as-xlangmessage.md)   
 [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md)
