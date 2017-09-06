---
title: "Interceptor Configuration Schema | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be33b0a4-49ea-48c8-8ae9-b050b6047cda
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Interceptor Configuration Schema
This section contains the common interceptor configuration schema.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema targetNamespace="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM/InterceptorConfiguration" elementFormDefault="qualified" xmlns="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM/InterceptorConfiguration" xmlns:tns="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM/InterceptorConfiguration" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="InterceptorConfiguration">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="EventSource" type="EventSourceType" minOccurs="1" maxOccurs="unbounded" />  
        <xs:element name="BamActivity" type="BamActivityType" minOccurs="1" maxOccurs="unbounded" />  
      </xs:sequence>  
    </xs:complexType>  
    <xs:key name="EventSourceNameKey">  
      <xs:selector xpath=".//tns:EventSource" />  
      <xs:field xpath="@Name" />  
    </xs:key>  
    <xs:key name="BamActivityNameKey">  
      <xs:selector xpath=".//tns:BamActivity" />  
      <xs:field xpath="@Name" />  
    </xs:key>  
  </xs:element>  
  
  <xs:complexType name="EventSourceType">  
    <xs:sequence>  
      <xs:any namespace="##any" processContents="lax" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="BAMEventSourceName" use="required" />  
    <xs:attribute name="Technology" type="TechnologyName" use="required" />  
    <xs:attribute name="Manifest" type="ManifestName" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="BamActivityType">  
    <xs:sequence>  
      <xs:element name="OnEvent" type="OnEventType" minOccurs="1" maxOccurs="unbounded">  
        <xs:keyref name="EventToEventSourceKeyRef" refer="EventSourceNameKey">  
          <xs:selector xpath="." />  
          <xs:field xpath="@Source" />  
        </xs:keyref>  
      </xs:element>  
    </xs:sequence>  
    <xs:attribute name="Name" type="BAMActivityName" use="required"/>  
  </xs:complexType>  
  
  <xs:complexType name="OnEventType">  
    <xs:sequence>  
      <xs:element name="Filter" type="DataEvaluationType" minOccurs="1" maxOccurs="1" />  
      <xs:element name="CorrelationID" type="DataEvaluationType" minOccurs="1" maxOccurs="1" />  
      <xs:element name="Update" type="UpdateType" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Reference" type="ReferenceType" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="ContinuationToken" type="DataEvaluationType" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="OnEventName" use="required" />  
    <xs:attribute name="Source" type="BAMEventSourceName" use="required" />  
    <xs:attribute name="IsBegin" type="xs:boolean" use="optional" default="false" />  
    <xs:attribute name="IsEnd" type="xs:boolean" use="optional" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="UpdateType">  
    <xs:complexContent>  
      <xs:extension base="DataEvaluationType">  
       <xs:attribute name="DataItemName" type="BAMAliasName" use="required" />  
       <xs:attribute name="Type" type="DataType" use="required" />  
      </xs:extension>  
    </xs:complexContent>  
  </xs:complexType>  
  
  <xs:simpleType name="DataType">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="NVARCHAR" />  
      <xs:enumeration value="DATETIME" />  
      <xs:enumeration value="INT" />  
      <xs:enumeration value="FLOAT" />  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:complexType name="ReferenceType">  
    <xs:sequence>  
      <xs:element name="Data" type="DataEvaluationType" minOccurs="1" maxOccurs="1" />  
      <xs:element name="LongData" type="DataEvaluationType" minOccurs="0" maxOccurs="1" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="BAMReferenceName" use="required" />  
    <xs:attribute name="Type" type="BAMReferenceType" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="DataEvaluationType">  
    <xs:sequence>  
      <xs:element name="Expression" type="DataExpressionType" minOccurs="1" maxOccurs="1" />  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:complexType name="DataExpressionType">  
    <xs:sequence>  
      <xs:any namespace="##any" processContents="lax" minOccurs="1" maxOccurs="unbounded" />  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:element name="Operation">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Argument" type="xs:string" minOccurs="0" maxOccurs="unbounded" />  
      </xs:sequence>  
      <xs:attribute name="Name" type="CommonOperationType" use="required" />  
    </xs:complexType>  
  </xs:element>  
  
  <xs:simpleType name="CommonOperationType">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Constant" />  
      <xs:enumeration value="Concatenate" />  
      <xs:enumeration value="And" />  
      <xs:enumeration value="Equals" />  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="BAMActivityName">  
    <xs:restriction base="BAMToken">  
      <xs:minLength value="1" />  
      <xs:maxLength value="48" />  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="BAMReferenceType">  
    <xs:restriction base="BAMToken">  
      <xs:minLength value="1" />  
      <xs:maxLength value="128" />  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="BAMReferenceName">  
    <xs:restriction base="BAMToken">  
      <xs:minLength value="1" />  
      <xs:maxLength value="128" />  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="BAMAliasName">  
    <xs:restriction base="BAMToken">  
      <xs:minLength value="1" />  
      <xs:maxLength value="50" />  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="BAMEventSourceName">  
    <xs:restriction base="BAMToken">  
      <xs:minLength value="1" />  
      <xs:maxLength value="128" />  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="OnEventName">  
    <xs:restriction base="BAMToken">  
      <xs:minLength value="1" />  
      <xs:maxLength value="128" />  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="ManifestName">  
    <xs:restriction base="xs:string">  
      <xs:minLength value="1" />  
      <xs:maxLength value="440" />  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TechnologyName">  
    <xs:restriction base="BAMToken">  
      <xs:minLength value="1" />  
      <xs:maxLength value="10" />  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="BAMToken">  
    <xs:restriction base="xs:string">  
      <xs:pattern value="(\p{Ll}|\p{Lu}|\p{Lo}|\p{Lt}|\p{Nl}|_)([ ]?(_|\p{L}|\p{Nl}|\p{Nd})+)*" />  
      <xs:whiteSpace value="preserve" />  
    </xs:restriction>  
  </xs:simpleType>  
  
</xs:schema>  
```  
  
## See Also  
 [Interceptor Configuration File](../core/interceptor-configuration-file.md)   
 [Windows Workflow Foundation Schema](../core/windows-workflow-foundation-schema.md)   
 [Windows Communication Foundation Schema](../core/windows-communication-foundation-schema.md)