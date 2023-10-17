---
description: "Learn more about: Value Mapping Functoid"
title: "Value Mapping Functoid"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Value Mapping Functoid
The **Value Mapping** functoid returns the value of its second parameter if its first parameter is true. A common use of the functoid is to change the attributes of a field into the attributes of a record. To flatten a portion of an input message by converting multiple records into a single record, use the [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md).  
  
 The following figure shows a map with the **Value Mapping** functoid used to change the attributes of a field into the attributes of a record.  
  
 ![Image that shows a map with the Value Mapping functoid used to change the attributes of a field into the attributes of a record.](../core/media/valuemappingfunctoid.gif "valuemappingfunctoid")  
Value Mapping Functoid Map  
  
 The following code shows an input instance message in which pairs of names and values are assigned to **Name** and **Value** attributes.  
  
```  
<ns0:Root xmlns:ns0="http://ValueMapping.WeatherIn">  
    <Record>  
        <Field Name="WindSpeed" Value="5"/>   
        <Field Name="Temperature" Value="20" />  
    </Record>  
    <Record>  
        <Field Name="WindSpeed" Value="15" />  
        <Field Name="Temperature" Value="18" />  
    </Record>  
</ns0:Root>  
```  
  
 The preceding map can convert this message into one in which the values are assigned to attributes with the corresponding names in separate records.  
  
```  
<ns0:Root xmlns:ns0="http://ValueMapping.WeatherOut">  
    <Record WindSpeed="5"/>  
    <Record Temperature="20"/>  
    <Record WindSpeed="15"/>  
    <Record Temperature="18"/>  
</ns0:Root>  
```  
  
 The **Equal** functoids test the values of the **Name** attribute. The first **Equal** functoid tests for the value of **Name** being "WindSpeed." When the **Name** is "WindSpeed," the first **Equal** functoid returns **True**. This, in turn, allows the **Value Mapping** functoid to set the value of the **WindSpeed** attribute in the output instance message.  
  
## Suppressing the Creation of Empty Tags  
 To suppress empty tags, use the Value Mapping functoid to control if a tag gets created or not. If the value is evaluated to true, the destination field will be created; otherwise the destination field will not be created. In a looping scenario, use a logical functoid and connect it to the destination record or field. If the condition is evaluated to false, the tag will not be created. For an example, see [Conditional Looping](../core/conditional-looping.md).  
  
## Forcing the Creation of Empty Tags  
 To force empty tags to be created, you can add a value in the Value property of the destination field or link a **Concatenate** functoid to the destination field.  In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], it is possible to force the generation of empty tags by selecting the "\<empty\>" value in the Value property of the destination field. In this case the field will be created with the empty value.  
  
## See Also  
 [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md)   
 [How to Add Value Mapping Functoids to a Map](../core/how-to-add-value-mapping-functoids-to-a-map.md)   
 [Advanced Functoids](../core/advanced-functoids.md)
