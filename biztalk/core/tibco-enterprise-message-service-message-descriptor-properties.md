---
description: "Learn more about: TIBCO Enterprise Message Service Message Descriptor Properties"
title: "TIBCO EMS Message Descriptor Properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# TIBCO Enterprise Message Service Message Descriptor Properties

## Descriptor properties, and values
The following table shows the complete set of available Message Descriptor (TibcoEMSMD structure) properties and their corresponding types and values.  
  
|Name|Type|Value|Notes|  
|----------|----------|-----------|-----------|  
|TibcoEMS .CorrelationID|string|||  
|TibcoEMS .DelieveryMode|string|One of PERSISENT or NON-PERSISTENT||  
|TibcoEMS .Destination|string||Read-only|  
|TibcoEMS .Expiration|long|||  
|TibcoEMS .MessageID|string||Read-only|  
|TibcoEMS .Priority|integer|From 0 to 9||  
|TibcoEMS .Redelivered|boolean||Read-only|  
|TibcoEMS .ReplyTo|string|Similar to Destination||  
|TibcoEMS .Timestamp|long||Read-only|  
  
 The read-only properties are those properties that are set by TIBCO Enterprise Message Service when the message is delivered to Microsoft BizTalk Adapter for TIBCO EMS. Changing the value, although it is possible in the expression of the message assignment shape, does not affect the message.  
  
 For other properties that must be moved from the EMS message to the BizTalk Server message, you must create a properties DLL and use it in the project.  
  
 The following sample properties schema enables the orchestration to use the `JMSXDeliveryCount` message property.  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://schemas.microsoft.com/BizTalk/TibcoEMS-properties" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:annotation>  
        <xs:appinfo>  
            <b:schemaInfo schema_type="property" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" />  
        </xs:appinfo>  
    </xs:annotation>  
    <xs:element name="JMSXDeliveryCount" type="xs:long">  
        <xs:annotation>  
            <xs:appinfo>  
                <b:fieldInfo propertyGuid="f62f1a4b-a528-45fb-b1f8-bd880e9f46db" />  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
</xs:schema>   
```  
  
 Make sure that the target namespace is used; only properties that use this namespace are copied to the BizTalk Server message or to the EMS message. See the BizTalk Server documentation for more information about message context properties.  
  
## See Also  
[TIBCO EMS message context properties](../core/message-context-properties-in-biztalk-server.md)
