---
title: "Configuration Properties for Integrated BizTalk Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapters, security"
  - "adapters, passwords"
  - "IReceiveLocation.CustomData property"
  - "security, passwords"
  - "ISendPort.CustomData property"
  - "binding files, passwords"
  - "adapters, properties"
  - "binding files, security"
ms.assetid: 4780a558-4322-428a-aa4a-0c32913faded
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuration Properties for Integrated BizTalk Adapters
The BizTalk Explorer object model exposes the **IReceiveLocation.CustomData** and **ISendPort.CustomData** properties that contain the adapter configuration property bag in the form of a name/value pair XML string. This name/value pair XML string is stored in a \<CustomProps\> element within a \<TransportTypeData\> element in a binding file. Most of the information in the \<CustomProps\> element corresponds to information that can be set for an adapter in the BizTalk Server user interface (such as the BizTalk Administration Console or BizTalk Explorer). If these values are present in a binding file then they are applied to the adapter configuration for the specified receive locations and send ports when the binding file is imported. Configuration information for all adapters is stored in the Single Sign-On database.  
  
 This section describes the configuration properties that can be set for each integrated BizTalk adapter.  
  
> [!NOTE]
>  Password information that is stored in the \<TransportTypeData\> element of a binding file is masked so that sensitive data is not saved in clear text. Depending on the transport, password information is either replaced with NULL or is replaced with asterisks. You must manually enter this information in the binding file to update the adapter configuration before importing the binding file into the target BizTalk Server configuration.  
  
 The configuration data for adapters built using the Adapter Framework is stored in an \<AdapterConfig\> element. Since the \<AdapterConfig\> element specifies the VT_BSTR (vt="8") data type, the **\< \>** characters contained in this element must be escaped or an error will occur when you attempt to import the binding file. This causes the text for the configuration data to be less human readable than if these characters were not escaped. The following example illustrates the effect of escaping these characters from sample configuration data for a send port bound to the POP3 adapter.  
  
 **TransportTypeData configuration data that does not escape the <> characters used in the \<AdapterConfig\> element**  
  
 This configuration data is invalid because the \<AdapterConfig\> element specifies the VT_BSTR (vt="8") data type and the \< \> characters contained in the \<AdapterConfig\> element are not escaped:  
  
```  
<TransportTypeData>  
<CustomProps>  
<AdapterConfig vt="8">  
<Config xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
<mailServer>test.microsoft.com</mailServer>  
<serverPort>0</serverPort>  
<userName>testuser</userName>  
<password>******</password>  
<authenticationScheme>Basic</authenticationScheme>  
<sslRequired>false</sslRequired>  
<applyMIME>true</applyMIME>  
<bodyPartContentType>text/xml</bodyPartContentType>  
<bodyPartIndex>1</bodyPartIndex>  
<errorThreshold>10</errorThreshold>  
<pollingInterval>5</pollingInterval>  
<pollingUnitOfMeasure>Minutes</pollingUnitOfMeasure>   
<uri>POP3://test.microsoft.com#testuser</uri>  
</Config>  
</AdapterConfig>  
</CustomProps>  
</TransportTypeData>  
```  
  
 **TransportTypeData configuration data that does escape the <> characters used in the \<AdapterConfig\> element**  
  
 Since the \<AdapterConfig\> element specifies the VT_BSTR (vt="8") data type, the \< \> characters must be escaped from the \<AdapterConfig\> element as seen below:  
  
```  
<TransportTypeData>  
<CustomProps>  
<AdapterConfig vt="8">  
<Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
xmlns:xsd="http://www.w3.org/2001/XMLSchema"><mailServer>test  
microsoft.com</mailServer><serverPort>0</serverPort>&  
lt;userName>testuser</userName><password>******</pass  
word><authenticationScheme>Basic</authenticationScheme>&  
lt;sslRequired>false</sslRequired><applyMIME>true</ap  
plyMIME><bodyPartContentType>text/xml</bodyPartContentType&  
gt;<bodyPartIndex>1</bodyPartIndex><errorThreshold>10  
</errorThreshold><pollingInterval>5</pollingInterval>  
<pollingUnitOfMeasure>Minutes</pollingUnitOfMeasure><uri  
>POP3://test.microsoft.com#testuser</uri></Config>  
</AdapterConfig>  
</CustomProps>  
</TransportTypeData>  
```  
  
 The integrated adapters that were created with the Adapter Framework include the following:  
  
- FTP Adapter  
  
- MQSeries Adapter  
  
- MSMQ Adapter  
  
- POP3 Adapter  
  
- Windows Sharepoint Services Adapter  
  
  To view a sample string used as the TransportTypeData configuration data for each integrated adapter, please see the configuration properties topic that is associated with the adapter in this section.  
  
## In This Section  
 [Configuration Property Variable Types](../core/configuration-property-variable-types.md)  
  
 [File Adapter Configuration Properties](../core/file-adapter-configuration-properties.md)  
  
 [FTP Adapter Configuration Properties](../core/ftp-adapter-configuration-properties.md)  
  
 [HTTP Adapter Configuration Properties](../core/http-adapter-configuration-properties.md)  
  
 [MQSeries Adapter Configuration Properties](../core/mqseries-adapter-configuration-properties.md)  
  
 [MSMQ Adapter Configuration Properties](../core/msmq-adapter-configuration-properties.md)  
  
 [POP3 Adapter Configuration Properties](../core/pop3-adapter-configuration-properties.md)  
  
 [SMTP Adapter Configuration Properties](../core/smtp-adapter-configuration-properties.md)  
  
 [SOAP Adapter Configuration Properties](../core/soap-adapter-configuration-properties.md)  
  
 [Windows Sharepoint Services Adapter Configuration Properties](../core/windows-sharepoint-services-adapter-configuration-properties.md)