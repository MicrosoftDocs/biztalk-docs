---
description: "Learn more about: Windows Workflow Foundation Schema"
title: "Windows Workflow Foundation Schema"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Windows Workflow Foundation Schema
This section contains the schema for the Windows Workflow Foundation interceptor.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema targetNamespace="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM/WorkflowInterceptorConfiguration" elementFormDefault="qualified" xmlns="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM/WorkflowInterceptorConfiguration" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
  <xs:element name="Operation">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Argument" type="xs:string" minOccurs="0" maxOccurs="unbounded" />  
      </xs:sequence>  
      <xs:attribute name="Name" type="WorkflowOperationType" use="required" />  
    </xs:complexType>  
  </xs:element>  
  
  <xs:simpleType name="WorkflowOperationType">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="GetActivityName" />  
      <xs:enumeration value="GetActivityEvent" />  
      <xs:enumeration value="GetWorkflowEvent" />  
      <xs:enumeration value="GetActivityType" />  
      <xs:enumeration value="GetUserDataType" />  
      <xs:enumeration value="GetUserKey" />  
      <xs:enumeration value="GetUserData" />  
      <xs:enumeration value="GetWorkflowProperty" />  
      <xs:enumeration value="GetActivityProperty" />  
      <xs:enumeration value="GetContextProperty" />  
    </xs:restriction>  
  </xs:simpleType>  
  
</xs:schema>   
```  
  
## See Also  
 [Interceptor Configuration Schema](../core/interceptor-configuration-schema.md)   
 [Windows Communication Foundation Schema](../core/windows-communication-foundation-schema.md)
