---
title: "Troubleshoot Operational Issues with the SAP adapter in BizTalk | Microsoft Docs"
description: Common errors, issues, and resolutions with mySAP adapter in BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb0f005b-7548-478b-8243-69e07c29d02c
caps.latest.revision: 32
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshoot Operational Issues with the SAP adapter
This section discusses using troubleshooting techniques to resolve operational errors that you might encounter when using [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].  
  
### Enable tracing  
 For information about tracing support in the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Diagnostic Tracing and Message Logging for the SAP adapter](../../adapters-and-accelerators/adapter-sap/diagnostic-tracing-and-message-logging-for-the-sap-adapter.md).  
  
##  <a name="client_dll"></a> Error loading the binding  
 **Problem**  
  
 When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the GUI gives the following error:  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **Cause**  
  
 When you start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] loads the adapter bindings for all the installed adapters. In turn, the adapter bindings are dependent on the specific client software for the enterprise application. You might face this issue for one or both of the following reasons:  
  
- The required LOB client software is not installed on the computer where you installed the adapter.  
  
- You did a Typical or Complete installation of the adapter, which installs all the adapters contained in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. However, the LOB client libraries might be installed for only one enterprise application. As a result, the GUI fails to load the bindings for the other adapters.  
  
  **Resolution**  
  
- Make sure you do a Custom installation of the adapters to install only the adapter you need.  
  
- Make sure the required LOB client versions are installed on the computer where you installed the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. [Supported LOB systems](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) lists the supported versions. The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] also requires certain DLLs to interface with the SAP system. For more information about the DLLs required by the adapter, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).
  
##  <a name="BKMK_SAPDisplay"></a> The SAP adapter is missing in BizTalk Administration console  
 **Problem**  
  
The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] included with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] does not show up in the list of adapters in the BizTalk Server Administration console.  
  
 **Cause**  
  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF custom binding. So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
 **Resolution**  
  
 You can explicitly add the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).  
  
##  <a name="BKMK_SAPConnOpen"></a> DLLs are missing error opening a connection to SAP  
 **Problem**  
  
 When you try to open a connection to the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], a dialog box appears in the SAP system, informing that some DLLs are missing.  
  
 **Cause**  
  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses librfc32u.dll to establish a connection with the SAP system. The librfc32u.dll, in turn, requires a set of DLLs to function. You get this error if these supporting DLLs are not added to the PATH variable on the computer where the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is installed.  
  
 **Resolution**  
  
 Refer to the table provided as a resolution to the [Error in loading the adapter bindings](#client_dll) issue. The table lists the supporting DLLs required to interface with the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
##  <a name="BKMK_SAPXmlRetrieve"></a> Error retrieving XML with more than 65,536 nodes  
 **Problem**  
  
 The adapter gives the following error while retrieving XML output that has more than 65,536 nodes.  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 **Cause**  
  
 The adapter cannot serialize and deserialize an object with more than 65,536 items.  
  
 **Resolution**  
  
 You can fix this issue by setting the `maxItemsInObjectGraph` parameter in either of the following two ways:  
  
- Set this parameter by changing the `maxItemsInObjectGraph` parameter in the `ServiceBehavior` attribute on your service class.  
  
- Add the following to your application's app.config file.  
  
  ```  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="NewBehavior">  
        <dataContractSerializer maxItemsInObjectGraph="65536000" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  ```  
  
  A sample app.config will look like the following.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
         <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <client>  
      <endpoint   behaviorConfiguration="NewBehavior" binding="sapBinding"  
       contract="IOutboundContract" name="sap_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
##  <a name="BKMK_SAPConnURI"></a> Error entering a connection URI for a WCF-Custom port in BizTalk Server  
 **Problem**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] gives the following error when you specify a connection URI to connect to the SAP system.  
  
```  
Error saving properties.  
(System.ArgumentException) The specified address is invalid.  
(System.ArgumentException) Invalid address;  
"<connection URI>" is not a well-formed absolute uri.  
```  
  
 **Cause**  
  
 The connection URI does not adhere to the standard encoding format. For example, the value for a parameter might contain a space.  
  
 **Resolution**  
  
 Make sure the connection URI you specify adheres to the standard encoding format. For example, a blank space must be replaced by "%20".  
  
##  <a name="BKMK_SAPOperate"></a> System.ArgumentNullException error while completing an operation on SAP  
 **Problem**  
  
 The adapter gives the following error when performing any operation on the SAP system using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
```  
System.ArgumentNullException: Value cannot be null.  
```  
  
 **Cause**  
  
 The WCF action for the message is not specified. WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.  
  
 **Resolution**  
  
 Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration. For instructions, see [Configure the SOAP action for the SAP system](../../adapters-and-accelerators/adapter-sap/configure-the-soap-action-for-the-sap-system.md). See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md) to see a list of actions for each operation.  
  
##  <a name="BKMK_SAPXmlParsing"></a> XmlReaderParsingException due to incorrect operation name in the specified action  
 **Problem**  
  
 The BizTalk Server Administration Console gives the following error when sending messages to an SAP system:  
  
```  
Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Invalid argument:  
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<operation_name>" Action="<action>" />  
</BtsActionMapping>  
```  
  
 **Cause**  
  
 If you configure a WCF-Custom port by importing the port binding file created by the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the action in the port is specified in the following format:  
  
```  
<BtsActionMapping>  
  <Operation Name="Op1" Action="http://MyService/Svc/Op1" />  
</BtsActionMapping>  
```  
  
 In the above format, the operation name is governed by the operation you chose while generating the schema. For example, if you generated schema for RFC_CUSTOMER_GET, the operation name in the action will be "RFC_CUSTOMER_GET". However, the operation name in the logical port created in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] might be different.  
  
 **Resolution**  
  
 Make sure the operation names in both the logical port (in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) and the physical port (in BizTalk Server Administration Console) are same.  
  
##  <a name="BKMK_SAPHundredCons"></a> Error opening more than 100 connections to SAP  
 **Problem**  
  
 The adapter throws the following exception when opening more than 100 connections to the SAP system.  
  
```  
Microsoft.ServiceModel.Channels.Common.ConnectionException: ErrorCode=RFC_OK. ErrorGroup=RFC_ERROR_COMMUNICATION. SapErrorMessage=Connect to SAP gateway failed  
Connect_PM  GWHOST=<gw_host>, GWSERV=<gw_serv>, SYSNR=<sys_number>  
LOCATION    CPIC (TCP/IP) on local host with Unicode  
ERROR       max no of 100 conversations exceeded  
```  
  
 **Cause**  
  
 By default, SAP does not enable more than 100 connections into the system.  
  
 **Resolution**  
  
 To increase the maximum number of connections, you must create an environment variable on the computer that has the SAP client libraries installed and set it to a numeric value. The value you specify for this environment variable is the maximum number of connections that can be made into the SAP system. Create the environment variable with the following details:  
  
- **Variable name**: CPIC_MAX_CONV  
  
- **Variable value**: any positive numeric value. For example, to enable 200 connections into the SAP system, specify the value as 200.  
  
  For instructions on creating an environment variable, see "How To Create System Variables in Windows 2000" at [http://go.microsoft.com/fwlink/?LinkId=95020](http://go.microsoft.com/fwlink/?LinkId=95020).  
  
##  <a name="BKMK_SAPIDOCMetadata"></a> Error generating or retrieving metadata for IDOCs  
 **Problem**  
  
 While generating metadata for the **Receive** operation for an IDOC in an SAP system, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] gives the following error.  
  
```  
Error while retrieving or generating the WSDL.  
Adapter message: Details: ErrorCode=RFC_EXCEPTION.  
ErrorGroup=RFC_ERROR_APPLICATION_EXCEPTION. SapErrorMessage= OBJECT_UNKNOWN.  
AdapterErrorMessage=Error returned by RfcCallReceiveEx while calling RFC: IDOCTYPE_READ_COMPLETE.  
```  
  
 **Cause**  
  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the IDOCTYPE_READ_COMPLETE RFC to retrieve the metadata for the **Receive** operation for an IDOC. Invoking this RFC requires specific user permissions in the SAP system. To generate metadata, if you have connected to the SAP system using a credential that does not have permission to invoke the IDOCTYPE_READ_COMPLETE RFC, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] gives an error.  
  
 **Resolution**  
  
 Log in to the SAP GUI using the same credentials you had used for the adapter. Navigate to transaction SE37, and enter the name of the RFC to execute as IDOCTYPE_READ_COMPLETE.  
  
 For the input parameters PI_IDOCTYP and PI_CIMTYP, enter the values corresponding to the custom IDoc. For the parameters PI_VERSION and PI_RELEASE, enter the same values as being chosen in the Adapter Metadata UI. And, press F8 to execute.  
  
 You should get the same exception as what the adapter receives, with more information about the issue.  
  
 If you are still not able to resolve the issue, generate a schema for the **ReceiveIdoc** operation instead of the **Receive** operation. In this case, the SAP adapter does not use IDOCTYPE_READ_COMPLETE, and does not throw any error.  
  
##  <a name="BKMK_SAPIDOCReceive"></a> Error sending or receiving IDOCs that have unreleased segments  
 **Problem**  
  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] gives an XmlReaderParsingException while sending IDOCs (using **Send** operation) or receiving IDOCs (using **Receive** operation) that have unreleased segments.  
  
 **Cause**  
  
 IDOCs are constituted of segments. While generating metadata, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] retrieves all the released segments that are present in the SAP system. However, when the adapter client uses the metadata to perform an operation such as receiving an IDOC, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] gives an XmlReaderParsingException. This occurs because when the IDOC is received, the SAP system might have sent some unreleased segments as well, the metadata for which was not generated by the adapter.  
  
 **Resolution**  
  
 Do any of the following:  
  
-   Upgrade your SAP system by applying appropriate patches for the unreleased segments.  
  
-   Use **SendIdoc** or **ReceiveIdoc** operations to send and receive IDOCs respectively. For more information about these operations, see [Operations on IDOCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).  
  
##  <a name="BKMK_SAPIDOCSend"></a> Error sending flat-file IDOCs to SAP that were received using the SAP FilePort  
 **Problem**  
  
 If you try to send (using **Send** operation) a flat-file IDOC to an SAP system that was generated using an SAP FilePort, the flat-file parser in the BizTalk orchestration fails to convert the flatf-file to an XML format, thereby failing the IDOD **Send** operation.  
  
 **Cause**  
  
 When the SAP system generates an IDOC using a FilePort, it trims off all the empty spaces at the end of a segment. However, the flat-file parser expects the data of the last field in the segment to be present to successfully convert the flat-file to XML. Because the empty spaces are not present in the segment, the flat-file parser fails to parse the flat-file to XML.  
  
 **Resolution**  
  
 For such flat-file IDOCs generated using the SAP FilePort, use the **SendIdoc** operation instead. For more information about this operation, see [Operations on IDOCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).  
  
##  <a name="BKMK_SAPRecIDOCCompat"></a> Error receiving IDOCs from SAP if EnableBizTalkCompatibilityMode property is set to true  
 **Problem**  
  
 The following exception is encountered while receiving an IDOC with the **EnableBizTalkCompatibilityMode** binding property set to true:  
  
```  
System.Exception: Loading property information list by namespace failed or property not found in the list. Verify that the schema is deployed properly.  
```  
  
 **Cause**  
  
 If the binding property **EnableBizTalkCompatibilityMode** is set to **true**, you must add the BizTalk property schema DLL for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] as a resource in your BizTalk application, that is, the application in which your project is deployed.  
  
 **Resolution**  
  
 The name for the BizTalk property schema for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is *Microsoft.Adapters.SAP.BiztalkPropertySchema.dll*. This is installed by the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup under \<installation drive\>:\ Program Files\Microsoft BizTalk Adapter Pack\bin. Perform the following tasks to add this assembly as a resource in your BizTalk application.  
  
#### Add an assembly as a resource in BizTalk application  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. In the console tree, expand **BizTalk Group**, expand **Applications**, and then the application to which you want to add a BizTalk assembly.  
  
3. Expand **Applications** and the application to which you want to add a BizTalk assembly.  
  
4. Right-click **Resources**, point to **Add**, and then click **BizTalk Assemblies**.  
  
5. Click **Add**, navigate to the folder containing the BizTalk assembly file, select the BizTalk assembly file, and then click **Open**.  
  
6. In **Options**, specify the options for installing the BizTalk assembly to the GAC, and then click **OK**.  
  
##  <a name="BKMK_SAPIDOCValidate"></a> Error in validation while receiving IDOCs from an SAP system  
 **Problem**  
  
 An IDOC received from an SAP system fails validation with an error similar to the following:  
  
```  
There was a failure executing the receive pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLReceive, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=<token>"  
Source: "Pipeline " Receive Port: "ReceiveIdoc" URI: "<connection uri>"  
Reason: The document failed to validate because of the following error:  
"The 'http://Microsoft.LobServices.Sap/2007/03/Types/Idoc/3/CREMAS03//620:TAXBS' element has an invalid value according to its data type."  
```  
  
 **Cause**  
  
 The metadata generated for receiving an IDOC contains the permissible values that can be received for a particular column as part of the receive operation. These values are exposed as enumeration in the generated metadata. However, when the IDOC is actually received, the value received could be different from the enumerated values. Hence the receive operation fails while validating the values. For example, in the above error message validation fails for the TAXBS column.  
  
 **Resolution**  
  
 You must manually edit the enumeration in schema (for BizTalk projects) or the client proxy (for .NET projects using WCF service model) to include the value received from the SAP system.  
  
##  <a name="BKMK_SAPFFIDOC"></a> Flat-file IDOCs, before and after converting to XML, are not identical  
 **Problem**  
  
 If you use a flat file parser to convert a flat-file IDOC to an XML using the schema, and then convert the XML back to a flat-file IDOC through a pipeline using the schema, the two flat-file IDOCs are not identical.  
  
 **Cause**  
  
 When generating the XML from a flat-file IDOC, the flat file parser does not generate the XML nodes with blank values. When this XML is converted back to a flat-file, the nodes missing from the XML are not reflected in the flat-file IDOC. Hence the flat-file IDOCs are not identical.  
  
 **Resolution**  
  
 In the schema used to convert the flat-file to XML and vice-versa, within the "Send" or "Receive" node definition, do the following:  
  
1. Set the **suppress_empty_nodes** property to **false** and set the **generate_empty_nodes** property to **true**. By default, the **suppress_empty_nodes** property is set to **true** and the **generate_empty_nodes** property is set to **false**, and hence all empty nodes are not reflected in the XML.  
  
2. The flat-file may contain an extra carriage return at the end. You can set the **suppress_trailing_delimiters** property to **Yes** to avoid this extra carriage return. This property is also exposed as the **Suppress Trailing Delimiters** property if you open the schema in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
##  <a name="BKMK_SAPAction"></a> Incorrect Action error using a physical port creating with a binding file  
 **Problem**  
  
 After you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate schema for a specific operation on the SAP system, the add-in also creates a port binding file. You can import this binding file using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create physical ports in BizTalk Server. However, when you send messages to the SAP system using such ports, the adapter fails to understand the action specified on the port and gives an error similar to the following:  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 **Cause**  
  
 When you create logical ports in a BizTalk orchestration, you specify certain names for the operations on those ports or you just use the default names like Operation_1, Operation_2, etc. However, in the binding file generated by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the operation name is same as the name of the operation for which you generate metadata. For example, if you generate metadata for RFC_CUSTOMER_GET, the action will be set to the following:  
  
```  
<Operation Name="RFC_CUSTOMER_GET" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET" />  
```  
  
 When you import the binding file, the same action is set on physical port. So, the operation names on the logical port (Operation_1, Operation_2, etc.) do not match the operation names specified in the action on the physical port, resulting in an error.  
  
 **Resolution**  
  
 Make sure the operation name in the logical port is the same as the operation name specified as part of the action in the physical port. Do one of the following:  
  
-   Change the operation name in the logical port in BizTalk orchestration from Operation_1, etc. to the operation for which you generate metadata, for example RFC_CUSTOMER_GET.  
  
-   Change the operation name in the action on the physical port to the operation name in the logical port. For example, you could change the action in the physical port to resemble the following:  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET" />  
    ```  
  
##  <a name="BKMK_SAPTableParams"></a> The response message for an operation ran on SAP does not contain any table parameters  
 **Cause**  
  
 If you use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to execute an operation on the SAP system that returns a large number of tables, and each table has a large number of records, that will amount to a large dataset being returned as part of the response message from the SAP system. So, by default, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not return any table parameters as part of the response message.  
  
 **Resolution**  
  
 You can request the tables that you want [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to return as part of the response. You can do so by providing an empty table parameter as part of the request message that you send to the SAP system. For example, `<table_parameter_name />`.  
  
##  <a name="BKMK_SAPIncorrectCreds"></a> Adapter Clients do not receive the response from SAP
 **Problem**  
  
 When using the adapters with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], if the credentials on the WCF-custom send port are incorrect, the request messages are not processed. After you specify the correct credentials, the message is sent to the SAP system and a response is received. However, the response message is not available to the out port.  
  
 **Resolution**  
  
 Restart the BizTalk host instance.  
  
##  <a name="BKMK_SAPInboundConn"></a> Connectivity issues receiving an inbound message from the SAP server  
 **Problem**  
  
 You get the following error only while receiving an inbound message from the SAP server using a WCF-Custom receive port for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
```  
The Messaging Engine failed to add a receive location "<location_name>" with URL "<connection URI>" to the adapter "WCF-Custom".  
Reason: "Microsoft.Adapters.SAP.RFCException: Details: ErrorCode=RFC_OK. ErrorGroup=RFC_ERROR_COMMUNICATION. SapErrorMessage=Connect to SAP gateway failed  
Connect_PM  TPNAME=<name>, GWHOST=<host>, GWSERV=<server>  
```  
  
 However, you are successfully able to send messages to the SAP system using a WCF-Custom send port.  
  
 **Resolution**  
  
 Install the SAP GUI on the same computer where you are running the adapter client and try receiving the inbound message again. For more information about how to install the SAP GUI, refer to SAP documentation.  
  
##  <a name="BKMK_SAPRootNode"></a> Error with RootNode TypeName in BizTalk Projects  
 **Problem**  
  
 In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **Resolution**  
  
1.  Right-click the rood node referenced in the error and select **Properties**.  
  
2.  For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).  
  
##  <a name="BKMK_SAPVS2008"></a> Invalid binding warning when using the adapter in Visual Studio  
 **Problem**  
  
 When you use the adapter to create an application in Visual Studio and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:  
  
```  
The element 'bindings' has invalid child element 'sapBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **Cause**  
  
 This warning appears because the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding, `sapBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].  
  
 **Resolution**  
  
 You can safely ignore this warning.  
  
##  <a name="BKMK_SAPSimilarSchema"></a> XLANG exception in BizTalk Server
 **Problem**  
  
 BizTalk Server throws an XLANG exception or an exception stating that the application cannot locate the document specification because multiple schemas matched the message type.  
  
 **Cause**  
  
 This happens because of either of the following:  
  
- You have generated more than one schema of a generic operation (such as SendIdoc and ReceiveIdoc) in a BizTalk Server project, deployed it to a BizTalk Server application, and then ran the application to perform respective operations on an SAP system. Because the schemas are common, there is a conflict between the schemas that are deployed in the BizTalk Server application.  
  
- In case of multiple projects, you have generated a generic operation schema for each of the BizTalk Server projects, deployed each project to a separate BizTalk Server application on the same host, and then ran an application or applications to perform respective operations on an SAP system. Because the schemas and assemblies are accessible across the applications in BizTalk Server, there is a conflict between the common schemas deployed under various BizTalk Server applications and assemblies.  
  
  **Resolution**  
  
  Use a single generic operation schema file for a BizTalk Server application. If you need to use a generic operation schema in multiple BizTalk Server applications on the same host, create an application containing a single generic operation schema, and then use the generic operation schema from all other applications in BizTalk Server.  
  
## See Also  
[Troubleshoot the SAP adapter](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)