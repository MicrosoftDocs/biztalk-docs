---
description: "Learn more about: SOAP Headers with Consumed Web Services"
title: "SOAP Headers with Consumed Web Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "SOAP headers, code samples"
  - "Web services, consuming"
  - "Web services, SOAP headers"
  - "SOAP headers, Web services"
  - "Web services, code samples"
ms.assetid: 7be2eee1-ce1c-4611-985c-91dbc8492d6e
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SOAP Headers with Consumed Web Services
After you add Web services to your orchestration using the **Add Web Reference** dialog box, you can use the SOAP headers that the Web Services Description Language (WSDL) defines in the Web service.

> [!NOTE]
>  Consumed Web services do not support unknown SOAP headers.

 The WSDL for the consumed Web service lists the defined SOAP headers in the binding element. The following example shows a binding element in the WSDL file for the consumed Web service:

```
<?xml version="1.0" encoding="utf-8"?>
<definitions xmlns:http="http://schemas.xmlsoap.org/wsdl/http/" xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" xmlns:s="http://www.w3.org/2001/XMLSchema" xmlns:s0="http://SOAPHeaderWS.ItemAvailability" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:tm="http://microsoft.com/wsdl/mime/textMatching/" xmlns:mime="http://schemas.xmlsoap.org/wsdl/mime/" targetNamespace="http://SOAPHeaderWS.ItemAvailability" xmlns="http://schemas.xmlsoap.org/wsdl/">
       <types>
             <s:schema elementFormDefault="qualified" targetNamespace="http://SOAPHeaderWS.ItemAvailability">

                    <s:element name="OrigDest" type="s0:OrigDest"/>
                    <s:complexType name="OrigDest">
                           <s:sequence>
                                 <s:element minOccurs="0" maxOccurs="1" name="Origination" type="s:string"/>
                                 <s:element minOccurs="0" maxOccurs="1" name="Destination" type="s:string"/>
                           </s:sequence>
                    </s:complexType>
             </s:schema>
       </types>

       <binding name="ItemAvailabilityServiceSoap" type="s0:ItemAvailabilityServiceSoap">
             <soap:binding transport="http://schemas.xmlsoap.org/soap/http" style="document"/>
             <operation name="ItemAvailability">
                    <soap:operation soapAction="http://SOAPHeaderWS.ItemAvailability/ItemAvailability" style="document"/>
                    <input>
                           <soap:body use="literal"/>
                           <soap:header message="s0:ItemAvailabilityOrigDest" part="OrigDest" use="literal"/>
                    </input>
                    <output>
                           <soap:body use="literal"/>
                           <soap:header message="s0:ItemAvailabilityOrigDest" part="OrigDest" use="literal"/>
                    </output>
             </operation>
       </binding>
       <service name="ItemAvailabilityService">
             <port name="ItemAvailabilityServiceSoap" binding="s0:ItemAvailabilityServiceSoap">
                    <soap:address location="http://localhost/SOAPHeaderWS/ItemAvailability.asmx"/>
             </port>
       </service>
</definitions>
```

 For more information about using SOAP headers, see "Using SOAP Headers" in .NET Framework documentation at [https://go.microsoft.com/fwlink/?LinkId=62266](https://go.microsoft.com/fwlink/?LinkId=62266).

## In This Section

-   [Consuming Web Services with SOAP Headers](../core/consuming-web-services-with-soap-headers.md)

-   [Using SOAP Headers in Orchestrations](../core/using-soap-headers-in-orchestrations.md)

-   [Using SOAP Headers in Pipeline Components](../core/using-soap-headers-in-pipeline-components.md)
