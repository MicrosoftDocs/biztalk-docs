---
title: "Windows Communication Foundation Schema | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e95e0e8d-82cf-4608-b54f-188cb8cdaaee
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Windows Communication Foundation Schema
This section contains the schema for the Windows Communication Framework interceptor.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema targetNamespace="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM/WcfInterceptorConfiguration"   
           xmlns="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM/WcfInterceptorConfiguration"   
           xmlns:xs="http://www.w3.org/2001/XMLSchema"  
           elementFormDefault="qualified" >  
  
  <xs:element name="Operation">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Argument" type="xs:string" minOccurs="0" maxOccurs="unbounded" />  
      </xs:sequence>  
      <xs:attribute name="Name" type="WcfOperationType" use="required" />  
    </xs:complexType>  
  </xs:element>  
  
  <xs:simpleType name="WcfOperationType">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="GetContextProperty" />  
      <xs:enumeration value="GetEndpointName" />  
      <xs:enumeration value="GetOperationName" />  
      <xs:enumeration value="GetServiceContractCallPoint" />  
      <xs:enumeration value="XPath" />  
      <xs:enumeration value="AutoGenerateCorrelationToken" />  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:element name="NamespaceMappings">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Namespace" type="WcfNamespaceMapping" minOccurs="1" maxOccurs="unbounded" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
  
  <xs:complexType name="WcfNamespaceMapping">  
    <xs:sequence>  
    </xs:sequence>  
    <xs:attribute name="Prefix" type="xs:string" use="required" />  
    <xs:attribute name="Uri" type="xs:string" use="required" />  
  </xs:complexType>  
  
</xs:schema>  
```  
  
## See Also  
 [Windows Workflow Foundation Schema](../core/windows-workflow-foundation-schema.md)   
 [Interceptor Configuration Schema](../core/interceptor-configuration-schema.md)