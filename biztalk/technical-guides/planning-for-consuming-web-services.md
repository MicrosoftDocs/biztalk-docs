---
title: "Planning for Consuming Web Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24863069-929b-4b0b-9643-073965fb5532
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for Consuming Web Services
Planning for Web services can be divided into two categories, planning for publishing Web services and planning for consuming Web services. This topic describes the considerations for consuming Web services. For information about publishing Web services, see [Planning for Publishing Web Services1](../technical-guides/planning-for-publishing-web-services1.md).  
  
 Keep the following in mind as you create your plan:  
  
- **Using Two Underscore Characters in a Parameter Name**  
  
   Parameter names for Web methods cannot begin with "__" (two underscore characters). Names that begin with two underscore characters may create Web message parts that are unsupported (unusable) by XLANG/s.  
  
- **The Any Element and the anyAttribute Attributes Are Not Supported in Web Methods**  
  
   You cannot use the **any** element or **anyAttribute** attribute in the schema for a Web method.  
  
- **Using XLANG/s Keywords**  
  
   A Web service name or a Web method name cannot be a keyword in an XLANG/s. If you use an XLANG/s keyword in the Web service name or Web method name, you will get a compilation error when you add the Web service. For a list of reserved words for the XLANG/s language, see the [XLANG/s Reserved Words](http://go.microsoft.com/fwlink/?LinkId=155765) (http://go.microsoft.com/fwlink/?LinkId=155765).  
  
- **Required XLANG/s Support for Parameter Types**  
  
   Using non-XLANG/s supported Web method parameter types will cause compilation errors. For example, BizTalk Server does not support a parameter that consists of a single dimensional array of schema types. In addition, BizTalk Server does not support multidimensional arrays. For a list of words that XLANG/s language reserves in BizTalk Server, see [XLANG/s Reserved Words](http://go.microsoft.com/fwlink/?LinkId=155765) (http://go.microsoft.com/fwlink/?LinkId=155765).  
  
- **Avoiding Compilation Errors Caused by Adding Web References Containing C# Keywords or Identifiers**  
  
   When you use the **Add Web Reference**to add Web references to BizTalk projects, BizTalk Server converts the schema types that are required to call each Web method to schemas. BizTalk Server adds these schemas to Reference.xsd. If your schemas contain element names that are C# keywords or the element name is not valid as a C# identifier, you may get a run-time error. To avoid run-time errors, ensure that the Web service you consume does not contain element names that are C# keywords or invalid C# identifiers.  
  
- **Multiple Service/Port Type Definitions Are Unsupported**  
  
   BizTalk Server supports adding a Web service file with a single service and port type definition. If you add a WSDL file with multiple service or port type definitions, you may receive the following error:  
  
   `Could not generate BizTalk files. Object reference not set to an instance of an object.`  
  
- **Support for Consuming Arrays Exposed by Web Services**  
  
   BizTalk Server can consume one dimensional and jagged arrays exposed by Web services that are not BizTalk Server Web services. For more information about how to consume Web service arrays, see [How to Consume Web Service Arrays](http://go.microsoft.com/fwlink/?LinkId=155766) (http://go.microsoft.com/fwlink/?LinkId=155766).  
  
  > [!NOTE]  
  >  Multi dimensional array syntax is not supported. For example, *MyArray[1,5]*.  
  
  > [!NOTE]  
  >  BizTalk Server does not support consuming an array of **DataSet** objects exposed by a Web service. The XLANG/s subservice does natively support the .NET DataSet class, but if you create a BizTalk project that contains a Web reference to a Web service that exposes an array of .NET DataSet objects you will get errors when you attempt to compile the project.  
  
- **Web Method Parameters Must be Xml Serializable**  
  
   All parameters in a consumed Web service must be Xml Serializable. If you add a Web method that contains a parameter that is not Xml Serializable, you may receive the following error message:  
  
   System.Xml.Element must be Xml Seralizeable to be a message part type.  
  
  > [!NOTE]  
  >  The data types, **XmlDocument** and **DataSet**, while not Xml Serializable, are supported.  
  
- **Consuming Messaging-Only Web Services**  
  
   When consuming messaging-only Web services, all BizTalk Server message body part names must match the Web method parameter names. For example, if the signature of the Web service is `WebMethod(MyType1 type1, MyType2 type2)`, the part name must be type1 and type2, you may get the following runtime error:  
  
   `Failed to retrieve the message part for parameter %1`  
  
   For more information, see [How to Consume Web Services in a Messaging-Only Scenario](http://go.microsoft.com/fwlink/?LinkId=155767) (http://go.microsoft.com/fwlink/?LinkId=155767).  
  
- **Configuring a SOAP Send Port Programmatically**  
  
   It is possible to set configuration properties programmatically on the message context. You can set these properties in an orchestration or a custom pipeline component whether the send port is static or dynamic.  
  
  > [!NOTE]  
  >  To configure the **MethodName** property for the static SOAP send port programmatically, you need to set **Method name** to **[Specify Later]** in the **Web Service** tab of the **SOAP Transport Properties** dialog box in the BizTalk Server Administration console.  
  
   For more information about the **MethodName** property, see [How to Dynamically Set the URI of a Consumed Web Service](http://go.microsoft.com/fwlink/?LinkID=155768) (http://go.microsoft.com/fwlink/?LinkID=155768).  
  
- **Property Rules**  
  
   If the configuration property is set in an orchestration or in a custom pipeline component in a receive pipeline, then the following rules are applied:  
  
  - If a message is sent to a static send port, the property value will be overwritten with the value configured for that send port.  
  
  - If a message is sent to a dynamic send port, the property value will not be overwritten.  
  
    If a configuration property is set in a custom pipeline component in a send pipeline, then the following rule is applied:  
  
  - The value will not be overwritten regardless of whether the message is sent to a static or dynamic send port. In other words, send pipeline components overwrite the configuration property no matter where it was set.  
  
  - For more information about custom pipeline components, see [Developing Custom Pipeline Components](http://go.microsoft.com/fwlink/?LinkId=155769) (http://go.microsoft.com/fwlink/?LinkId=155769).  
  
  - For more information about the configuration properties of the SOAP send adapter, see [How to Dynamically Set the URI of a Consumed Web Service](http://go.microsoft.com/fwlink/?LinkID=155768) (http://go.microsoft.com/fwlink/?LinkID=155768).  
  
- **Adding a Web Reference to a Consumed Web Service That Contains a Multi-Rooted Schema Will Cause a Compilation Error**  
  
   If you add a Web reference to your project for a Web service that was derived from a published BizTalk orchestration and the orchestration contains a schema with multiple roots, then an error will occur when the project is compiled. If you add a Web reference to your project that was derived from a published BizTalk orchestration, ensure that the orchestration does not contain any multi-rooted schemas.  
  
- **Using TypedDataSets as Parameters to Web Methods**  
  
   The following is what you need to do to support using TypedDataSets as parameters to Web methods:  
  
  1.  Add the Web reference to a C# project and then generate the proxy.  
  
  2.  Create a SOAP send port and specify the proxy on the send port and choose the method.  
  
  3.  In the orchestration, define a late bound port and define the message types. For most cases where no property promotion or distinguished field access is needed, the type can be defined as **XMLDocument**. Select PassThrough pipelines with this type.  
  
  4.  In the BizTalk Server Administration console, in the **Web Service** tab in the **SOAP Transport Properties** dialog box of the SOAP send port, specify that you want to use that proxy that you created. You will also need to specify assembly, type, and method.  
  
- **Adding a Web Reference to a Consumed Web Service that Contains a Web Method Expecting Generic-Based Parameters Will Cause a Compilation Error**  
  
   If you add a Web reference to your project for a Web service that contains a Web method expecting generic-based parameters such as nullable parameters, an error will occur when the project is compiled. This is not supported. You must use explicit specialization to call the generic class from XLANG/s.  
  
- **BizTalk Schema Generation Using the Add Web Reference**  
  
   When you use the **Add Web Reference**to add Web references to BizTalk projects, BizTalk Server converts the schema types that are required to call each Web method to schemas. BizTalk Server adds these schemas to Reference.xsd. To ensure that the **Add Web Reference** generates the BizTalk schemas correctly, the Web services must conform to the following guidelines:  
  
  -   Web methods should have **SoapDocumentMethodAttribute** instead of **SoapRpcMethodAttribute**.  
  
  -   Web services and methods must use the **Literal** binding instead of **Encoded** such as **[SoapDocumentMethod(Use=SoapBindingUse.Literal)]**.  
  
  -   Web method parameters and return types must have **XmlRootAttribute** with a valid **Namespace** property unless they are native XSD types and the XmlNode type.  
  
  -   Web methods must not use the **RequestNamespace** and **ResponseNamespace** properties in **SoapDocumentMethodAttribute**.  
  
  -   Web services must be compliant with the Web services interoperability (WSI) Basic Profile version 1.1.  
  
- **The Add Web Reference Does Not Support the Web Services Description Language (WSDL) Import Element**  
  
   The Add Web Reference fails when you add Web references for the WSDL file with the import element.  
  
## See Also  
 [Planning the BizTalk Server Tier](../technical-guides/planning-the-biztalk-server-tier.md)