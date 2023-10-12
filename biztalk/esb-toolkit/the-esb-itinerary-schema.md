---
description: "Learn more about: The ESB Itinerary Schema"
title: "The ESB Itinerary Schema"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The ESB Itinerary Schema
The ESB Itinerary schema named Itinerary.xsd defines an itinerary as a set of processing instructions, generally referred to as itinerary services. An itinerary service may contain one or more itinerary services and the corresponding resolver connection strings, as shown in the following schema definition.  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://schemas.microsoft.biztalk.practices.esb.com/itinerary" targetNamespace="http://schemas.microsoft.biztalk.practices.esb.com/itinerary" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
  <xs:annotation>  
    <xs:appinfo>  
      <b:schemaInfo root_reference="Itinerary" xmlns:b="http://schemas.microsoft.con/BizTalk/2003" />  
    </xs:appinfo>  
  </xs:annotation>  
  <xs:element name="Itinerary">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="BizTalkSegment">  
          <xs:complexType>  
            <xs:attribute name="interchangeId" type="xs:string" />  
            <xs:attribute name="epmRRCorrelationToken" type="xs:string" />  
            <xs:attribute name="receiveInstanceId" type="xs:string" />  
            <xs:attribute name="messageId" type="xs:string" />  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="ServiceInstance">  
          <xs:complexType>  
            <xs:attribute name="uuid" type="xs:string" />  
            <xs:attribute name="name" type="xs:string" />  
            <xs:attribute name="type" type="xs:string" />  
            <xs:attribute name="state" type="xs:string" />  
            <xs:attribute name="position" type="xs:int" />  
            <xs:attribute name="isRequestResponse" type="xs:boolean" />  
            <xs:attribute name="stage" type="Stages" />  
          </xs:complexType>  
        </xs:element>  
        <xs:element minOccurs="1" maxOccurs="unbounded" name="Services">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="Services">  
                <xs:complexType>  
                  <xs:sequence>  
                    <xs:element minOccurs="0" maxOccurs="1" name="PropertyBag" nillable="true">  
                      <xs:complexType>  
                        <xs:sequence minOccurs="0" maxOccurs="1">  
                          <xs:element minOccurs="0" maxOccurs="unbounded" name="Property">  
                            <xs:complexType>  
                              <xs:attribute name="name" type="xs:string" use="required" />  
                              <xs:attribute name="value" type="xs:string" use="required" />  
                            </xs:complexType>  
                          </xs:element>  
                        </xs:sequence>  
                      </xs:complexType>  
                    </xs:element>  
                  </xs:sequence>  
                  <xs:attribute name="uuid" type="xs:string" />  
                  <xs:attribute name="beginTime" type="xs:string" />  
                  <xs:attribute name="completeTime" type="xs:string" />  
                  <xs:attribute name="name" type="xs:string" />  
                  <xs:attribute name="type" type="xs:string" />  
                  <xs:attribute name="state" type="xs:string" />  
                  <xs:attribute name="resolve" type="xs:boolean" />  
                  <xs:attribute name="isRequestResponse" type="xs:boolean" />  
                  <xs:attribute name="position" type="xs:int" />  
                  <xs:attribute name="serviceInstanceId" type="xs:string" />  
                  <xs:attribute name="isTrackingEnabled">  
                    <xs:simpleType>  
                      <xs:restriction base="xs:boolean" />  
                    </xs:simpleType>  
                  </xs:attribute>  
                  <xs:attribute name="stage" type="Stages" />  
                </xs:complexType>  
              </xs:element>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="ResolverGroups">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element maxOccurs="unbounded" name="Resolvers">  
                <xs:complexType>  
                  <xs:simpleContent>  
                    <xs:extension base="xs:string">  
                      <xs:attribute name="serviceId" type="xs:string" />  
                    </xs:extension>  
                  </xs:simpleContent>  
                </xs:complexType>  
              </xs:element>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
      <xs:attribute name="uuid" type="xs:string" />  
      <xs:attribute name="beginTime" type="xs:string" />  
      <xs:attribute name="completeTime" type="xs:string" />  
      <xs:attribute name="state" type="xs:string" />  
      <xs:attribute name="isRequestResponse" type="xs:boolean" />  
      <xs:attribute name="servicecount" type="xs:int" use="required" />  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="Stages">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="notSpecified" />  
      <xs:enumeration value="receiveInbound" />  
      <xs:enumeration value="receiveTransmit" />  
      <xs:enumeration value="sendTransmit" />  
      <xs:enumeration value="sendInbound" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
 The **ServiceInstance** element corresponds to the current itinerary service and contains properties such as **name**, **type**, **state**, and **position** that the service promotes into the message context. The schema named System-Properties.xsd in the **Microsoft.Practices.ESB.ItinerarySchemas** assembly defines these properties.  
  
 The **Services** element represents a set of itinerary services, with each service defined by its state, begin time, completion time, type (**Orchestration** or **Messaging**), and, optionally, stage (**receiveInbound**, **receiveTransmit**, **sendTransmit**, **sendInbound**).  
  
 The **ResolverGroups** element contains multiple **Resolvers** elements, each of which defines one or more resolver connection strings that an itinerary references through the **serviceid** attribute.  
  
 The following shows a sample of a submitted itinerary SOAP header before it is processed by the ESB Itinerary Pipeline component.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Itinerary xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" uuid="" beginTime="" completeTime="" state="Pending" isRequestResponse="false" xmlns="http://schemas.microsoft.biztalk.practices.esb.com/itinerary">  
  
  <ServiceInstance uuid="" name="Microsoft.Practices.ESB.Services.Transform" type="Messaging" state="Pending" position="0" isRequestResponse="false" xmlns="" />  
  
  <Services xmlns="">  
    <Service uuid="" beginTime="" completeTime="" name="Microsoft.Practices.ESB.Services.Transform" type="Messaging" state="Pending" isRequestResponse="false" position="0" serviceInstanceId="" />  
  </Services>  
  
  <Services xmlns="">  
    <Service uuid="" beginTime="" completeTime="" name="DynamicResolutionSolicitResp" type="Messaging" state="Pending" isRequestResponse="true" position="1" serviceInstanceId="" />  
  </Services>  
  
  <ResolverGroups xmlns="">  
    <Resolvers serviceId="DynamicResolutionSolicitResp1"><![CDATA[BRE:\\policy=GetCanadaEndPoint;version=;useMsg=;]]></Resolvers>  
  
    <Resolvers serviceId="Microsoft.Practices.ESB.Services.Transform0"><![CDATA[BRE:\\policy=CanadaSubmitOrderMaps;version=;useMsg=;]]></Resolvers>  
  </ResolverGroups>  
  
</Itinerary>  
```
