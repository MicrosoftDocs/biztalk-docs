---
title: "Using Distinguished Fields and Property Fields | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, distinquished fields"
  - "messages, properties"
ms.assetid: 264ee15e-be9a-4ba2-9c61-a1570b20378e
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Distinguished Fields and Property Fields
Distinguished fields are message data of special interest that you use primarily to make decisions or to manipulate data in your orchestration.  
  
 Message properties are either data—contents of the message itself—or "metadata"—context information about the message such as time stamps or routing information. You can use system-defined message context properties or transport context properties, or you can define your own properties by making reference to schema fields from within a property schema. Properties are used in subscriptions and correlations.  
  
-   You can designate a field in a schema as a distinguished field or property field by using the **Promote Properties** dialog box from within the Editor. For more information, see [Promoting Properties](../core/promoting-properties.md)  
  
-   You can designate a field in a .NET type as a distinguished field by decorating it with the DistinguishedField attribute, or as a property by the Property attribute.  
  
## Using Distinguished Fields  
 Distinguished fields are referred to by the path to the field in the message, using periods to separate the message name, the names of any records that enclose the field, and the name of the field itself:  
  
```  
MyMessage.MyRecord.MySubrecord.MyDistinguishedField  
```  
  
## Using Property Fields  
 Once you have added a field to a property schema, its value can be accessed in the orchestration with code and in filter expressions. For more information about property schemas, see [Property Schemas](../core/property-schemas.md).  
  
> [!NOTE]
>  Message content or data properties are essentially shortcuts to the underlying data: if you modify the property, the data will be modified, and vice versa.  
  
 Message properties are referred to by the name of the message followed by the namespace (the schema) and property name in parentheses:  
  
```  
MyMessage(Invoice.PropertySchema.InvoiceID)  
```  
  
> [!NOTE]
>  When you use a reserved keyword as the name of a field in a schema, and you promote the field by selecting Quick Promotion, the property name of the field is changed to __\<Reserved Keyword>. (The double underscore is added before the property name.) However, if you use this property name in an orchestration expression, you will receive a compiler error when building the orchestration.  To work around this error, you need to manually add @ before the double underscore. For example,  
>   
>  `MyMessage(Invoice.PropertySchema.@__Name) = "Product Name";`  
  
## Property Sets  
 You can also assign all of the context properties of one message (a property set) to the context properties of another message. To assign a property set, you simply place an asterisk in parentheses after both message names, in the same way you would put a property in parentheses:  
  
```  
MyMessage2(*)=MyMessage1(*);  
```  
  
 After the property set has been assigned to MyMessage2 in the example, all of the properties in MyMessage2 contain the same values as the properties in MyMessage1.  
  
## See Also  
 [Promoting Properties](../core/promoting-properties.md)   
 [Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md)   
 [Using Messages in Orchestrations](../core/using-messages-in-orchestrations.md)   
 [About BizTalk Message Context Properties](../core/about-biztalk-message-context-properties.md)