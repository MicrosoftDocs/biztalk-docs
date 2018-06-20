---
title: "Troubleshoot Operational Issues with the Siebel adapter in BizTalk | Microsoft Docs"
description: Common issues and resolutions for Siebel adapter in the BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 74d152d9-9893-4f93-894a-350bae8be7bd
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshoot Operational Issues with the Siebel adapter
This section provides a centralized location for information about operational issues you might encounter when using the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].  
  
## Enabling Tracing  
 For information about tracing support in the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Diagnostic Tracing and Message Logging for the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/diagnostic-tracing-and-message-logging-for-the-siebel-adapter.md).  
  
## Known Issues  
 The following are some issues and recommended solutions that you might encounter while using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
  
###  <a name="BKMK_SiebelBindingError"></a> Error in loading the adapter bindings  
 **Problem**  
  
 When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the GUI gives the following error:  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **Cause**  
  
 When you start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF loads the adapter bindings for all the installed adapters. In turn, the adapter bindings are dependent on the specific enterprise application client software. So, you could face this issue for one or both of the following reasons:  
  
- The required LOB client software is not installed on the computer where you installed the adapter.  
  
- You did a "Typical" or "Complete" installation of the adapter, which installs all the adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. However, the client libraries might be installed for only one enterprise application. As a result, the GUI fails to load the bindings for the other adapters.  
  
  **Resolution**  
  
- Make sure the required client versions are installed on the computer where you installed the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].  
  
- Make sure you do a custom installation of the adapters to install only the adapter you need.  
  
###  <a name="BKMK_SiebelDispAdap"></a> The Siebel adapter does not display in the list of adapters in BizTalk Server Administration console  
 **Problem**  
  
 Unlike the earlier version of the adapters that shipped with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] that shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] does not show up in the list of adapters in the BizTalk Server Administration console.  
  
 **Cause**  
  
 The latest [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is a WCF custom binding. So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
 **Resolution**  
  
 You can explicitly add the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).  
  
###  <a name="BKMK_SiebelConnecting"></a> Error while connecting to the Siebel system  
 **Problem**  
  
 The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] gives the following error when you try to connect to the Siebel system:  
  
```  
Connecting to the system LOB has failed. Retrieving the COM class factory for component with CLSID {ID} failed due to the following error: 80040154  
```  
  
 **Cause**  
  
 The Siebel Web client might not be installed on the computer.  
  
 **Resolution**  
  
 Make sure the supported version of the Siebel Web client is installed on the computer. Refer to the installation guide for supported client and server versions for Siebel. The installation guide is available at \<system drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.  
  
###  <a name="BKMK_SiebelXMLRetrieve"></a> Error while retrieving XMLs with more than 65536 nodes  
 **Problem**  
  
 The adapter gives the following error while retrieving XML output that has more than 65536 nodes.  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 **Cause**  
  
 The adapter cannot serialize and deserialize an object with more than 65536 items.  
  
 **Resolution**  
  
 You can fix this issue by setting the `maxItemsInObjectGraph` parameter. You can set this in any of the following two ways:  
  
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
  
  A sample app.config will look like:  
  
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
      <endpoint   behaviorConfiguration="NewBehavior" binding="siebelBinding"  
       contract="IOutboundContract" name="siebel_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
###  <a name="BKMK_SiebelConnURI"></a> Error while specifying a connection URI for a WCF-Custom port in BizTalk  
 **Problem**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] gives the following error when you specify a connection URI to connect to the Siebel system.  
  
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
  
###  <a name="BKMK_SiebelPerfOps"></a> Error while performing operation on the Siebel system  
 **Problem**  
  
 The adapter gives the following error when performing any operation on the Siebel system using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
- **For BizTalk Server**  
  
  ```  
  System.ArgumentNullException: Value cannot be null.  
  ```  
  
  **Cause**  
  
  The WCF action for the message is not specified. WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.  
  
  **Resolution**  
  
  Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration. For instructions, see [Configure the SOAP action for Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-soap-action-for-siebel.md). See [Messages and message schemas](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) for a list of actions for each operation.  
  
###  <a name="BKMK_SiebelXmlParsing"></a> XmlReaderParsingException due to an incorrect operation name in the specified action  
 **Problem**  
  
 The BizTalk Server Administration console gives the following error when sending messages to a Siebel system:  
  
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
  
 In the preceding format, the operation name is governed by the operation you chose while generating the schema. For example, if you generated schema for a Query operation on a Siebel business component, the operation name in the action will be "Query". However, the operation name in the logical port created in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] might be different.  
  
 **Resolution**  
  
 Make sure the operation names in both the logical port (in the BizTalk orchestration in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) and the physical port (in BizTalk Server Administration console) are the same.  
  
###  <a name="BKMK_SiebelTerminate"></a> Application using the Siebel adapter does not terminate  
 **Problem**  
  
 An application that uses the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Siebel client version 7.5 does not terminate.  
  
 **Cause**  
  
 This is because of a Siebel client issue where the process does not terminate when logging off from a Siebel server.  
  
 **Resolution**  
  
 Make sure you have the patch 7.5.3.17 installed for the Siebel server, along with the quick fix QF0H05.  
  
###  <a name="BKMK_SiebelHang"></a> Siebel adapter may hang if the Siebel server is restarted  
 **Problem**  
  
 If the Siebel server is restarted while the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is sending a message to the Siebel server using, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] may hang.  
  
 **Resolution**  
  
 Restart the BizTalk application host instance. To do so from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, in the console tree expand **BizTalk Group**, expand **Platform Settings**, and then click **Host Instances**. From the right pane, right-click the host name, and then select **Restart**.  
  
###  <a name="BKMK_SiebelAction"></a> The adapter does not recognize the action on the physical port even though you use the binding file generated by the Consume Adapter Service add-in to create the ports  
 **Problem**  
  
 After you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate schema for a specific operation on the Siebel system, the add-in also creates a port binding file. You can import this binding file using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create physical ports in BizTalk Server. However, when you send messages to the Siebel system using such ports, the adapter fails to understand the action specified on the port and gives an error similar to the following:  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 **Cause**  
  
 When you create logical ports in a BizTalk orchestration, you specify certain names for the operations on those ports or you just use the default names like Operation_1, Operation_2, etc. However, in the binding file generated by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the operation name is same as the name of the operation for which you generate metadata. For example, if you generate metadata for Insert operation on the Account business component, the action will be set to the following:  
  
```  
<Operation Name="Insert" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert" />  
```  
  
 When you import the binding file, the same action is set on physical port. So, the operation names on the logical port (Operation_1, Operation_2, etc.) do not match the operation names specified in the action on the physical port, resulting in an error.  
  
 **Resolution**  
  
 Make sure the operation name in the logical port is the same as the operation name specified as part of the action in the physical port. Do one of the following:  
  
-   Change the operation name in the logical port in BizTalk orchestration from Operation_1, etc. to the operation for which you generate metadata, for example Insert.  
  
-   Change the operation name in the action on the physical port to the operation name in the logical port. For example, you could change the action in the physical port to resemble the following:  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert" />  
    ```  
  
###  <a name="BKMK_SiebelXMLEncode"></a> Siebel adapter does not handle Siebel objects with XML encoded strings in the name  
 **Problem**  
  
 The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] cannot perform operations involving Siebel objects (business objects, business components, business services, picklist, methods, fields, arguments, etc) that have XML encoded strings in their name. For example, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] will not be able to invoke a business service method with the name Time_x0020_Stamp.  
  
 **Resolution**  
  
 Make sure the Siebel objects do not contain XML encoded strings in their name.  
  
###  <a name="BKMK_SiebelRootNode"></a> Error with RootNode TypeName in BizTalk Projects  
 **Problem**  
  
 In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **Resolution**  
  
1.  Right-click the rood node referenced in the error and select **Properties**.  
  
2.  For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).  
  
###  <a name="BKMK_SiebelVS2008"></a> Invalid binding warning when using the adapter in Visual Studio  
 **Problem**  
  
 When you use the adapter to create an application in Visual Studio and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:  
  
```  
The element 'bindings' has invalid child element 'siebelBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **Cause**  
  
 This warning appears because the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding, `siebelBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].  
  
 **Resolution**  
  
 You can safely ignore this warning.  
  
## See Also  
[Troubleshoot the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)