---
description: "Learn more about: Describe the WSDL PortType Documentation Schema with the WCF LOB Adapter SDK"
title: "Describe the WSDL PortType Documentation Schema with the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9dd96eaf-b3b3-49b4-aea9-0ae1e8999d62
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Describe the WSDL PortType Documentation Schema with the WCF LOB Adapter SDK
The WSDL that the  [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] generates contains additional descriptive information for each portType. The schema for this additional information is described in this topic.  
  
## Documentation XML Schema  
 The operation documentation is implemented using annotation of the portType to add a node that represents the adapter documentation for the operation. This node contains subnodes that further describe the operation and parameters. This schema is defined as follows.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="adapterOperationDocumentation">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="summary" type="xs:string" />  
        <xs:element maxOccurs="unbounded" name="param">  
          <xs:complexType>  
            <xs:simpleContent>  
              <xs:extension base="xs:string">  
                <xs:attribute name="name" type="xs:string" use="required" />  
              </xs:extension>  
            </xs:simpleContent>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="returns" type="xs:string" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 When WSDL is generated for a given operation, the preceding schema is used to provide additional descriptive information in human readable format. For example, the following portType information is returned for the EchoString operation of the Echo Adapter.  
  
```  
<wsdl:portType name="EchoService">  
  <wsdl:operation name="EchoString">  
    <wsdl:documentation>  
      <doc:adapterOperationDocumentation>  
        <doc:summary>String EchoString( string aName)\</doc:summary>  
        <doc:param name="aName">This string will be echoed back to the user.\</doc:param>  
        <doc:returns>String value containing the value of aName \</doc:returns>  
      </doc:adapterOperationDocumentation>  
    </wsdl:documentation>  
    <wsdl:input wsaw:Action="Echo/EchoString" message="ns2:EchoService_EchoString_InputMessage" />  
    <wsdl:output wsaw:Action="Echo/EchoString/response" message="ns2:EchoService_EchoString_OutputMessage" />  
  </wsdl:operation>  
</wsdl:portType>  
```  
  
 The values for the documentation elements are obtained from `Microsoft.ServiceModel.Channels.Common.ParameterizedOperationMetadata` for the operation. The preceding example was generated as a result of the following example.  
  
```csharp  
ParameterizedOperationMetadata om = new ParameterizedOperationMetadata(operationId, operationId);  
// set this if you want this operation to belong to this interface name  
// in the generated proxy, the interface name will be EchoService  
// and the client implementation name will be EchoServiceClient.  
om.OperationGroup = "EchoService";  
// set the operation namespace to be same as service namespace  
om.OperationNamespace = EchoAdapter.SERVICENAMESPACE;              
switch (operationId)  
{  
   case "Echo/EchoString":  
       om.DisplayName = "EchoString";  
       om.OriginalName = "targetSystemEchoString";  
       om.Description = "String EchoString( string aName)";  
       OperationParameter parm1 = new OperationParameter("aName", OperationParameterDirection.In, QualifiedType.StringType, false);  
       parm1.Description = "This string will be echoed back to the user.";  
       OperationResult result = new OperationResult(new SimpleQualifiedType(XmlTypeCode.String), false);  
       result.Description = "String value containing the value of aName";  
       om.Parameters.Add(parm1);  
       om.OperationResult = result;  
       return om;   
```  
  
## See Also  
 [Development best practices using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)
