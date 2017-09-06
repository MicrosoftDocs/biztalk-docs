---
title: "POP3 Adapter Configuration Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive locations, adapters"
  - "POP3 adapters, receive locations"
  - "POP3 adapters, code sample"
  - "POP3 adapters, properties"
ms.assetid: e30c848d-afff-42f3-8162-c7ea8c7e3b9a
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# POP3 Adapter Configuration Properties
The following table lists the configuration properties that you can set for a POP3 adapter receive location:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|mailServer|VT_BSTR|Specify the POP3 mail server that houses the mailbox that will be polled by the POP3 adapter.|None|None|  
|serverPort|VT_BSTR|Specify the port for the POP3 mail server.|Valid values are from 0 to 65535.|A value of 0 indicates to use the default POP3 port of 110 if the sslRequired property is set to false or port 995 if the sslRrequired property is set to true.<br /><br /> The default value is 0.|  
|userName|VT_BSTR|Specify the user name to use for authentication with the POP3 server.|None|None|  
|password|VT_BSTR|Specify the user password to use for authentication with the POP3 server.|This value is always masked when exporting a binding file. This field must be manually populated with the password before importing the binding file into the target BizTalk Server configuration.|None|  
|authenticationScheme|VT_BSTR|Specify the type of authentication to use with the destination server.|Valid values are:<br /><br /> -   Basic<br />-   Digest<br />-   SPA|There is not a default value for this property.|  
|sslRequired|VT_BSTR|Specify whether to use SSL to communicate with the destination server.|Valid values are:<br /><br /> -   true<br />-   false|The default value is false.|  
|applyMIME|VT_BSTR|Specify whether to apply MIME decoding to messages received by the POP3 adapter.|Valid values are:<br /><br /> -   true<br />-   false|The default value is true.|  
|bodyPartContentType|VT_BSTR|Specify the body part content type of the incoming e-mail message to submit to BizTalk Server.|Valid values are:<br /><br /> -   body<br />-   text/xml<br />-   text/plain<br />-   text/|There is not a default value for this property.|  
|bodyPartIndex|VT_BSTR|Specify the body part of the incoming e-mail message to submit to BizTalk Server.|Valid values are from 0 to 128.|The default value is 0.|  
|errorThreshold|VT_BSTR|Specify the maximum number of network or protocol errors to wait before shutting down the adapter.|Valid values are from 0 to 4294967295.|Specify a value of 0 to prevent the adapter from shutting down.<br /><br /> The default value is 10.|  
|pollingInterval|VT_BSTR|Specify the interval between attempts to retrieve messages from the POP3 server.|Valid values are:<br /><br /> -   From 1 to 120 if the pollingUnitOfMeasure value is Days.<br />-   From 1 to 2880 if the pollingUnitOfMeasure value is Hours.<br />-   From 1 to 172800 if the pollingUnitOfMeasure value is Minutes.<br />-   From 2 to 10368000 if the pollingUnitOfMeasure value is Seconds.|The default value is 5.|  
|pollingUnitOfMeasure|VT_BSTR|Specify the unit of measure to be used in conjunction with the value for pollingInterval.|Valid values are:<br /><br /> -   Days<br />-   Hours<br />-   Minutes<br />-   Seconds|The default value is Minutes.|  
|uri|VT_BSTR|Specify the full path to the mailbox monitored by the receive location.|The URI for a send port or receive location cannot exceed 256 characters.|None|  
  
 The following code shows the format of the string you use to set the properties:  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><mailServer>test.microsoft.com</mailServer><serverPort>0</serverPort><userName>testuser</userName><password>******</password><authenticationScheme>Basic</authenticationScheme><sslRequired>false</sslRequired><applyMIME>true</applyMIME><bodyPartContentType>text/xml</bodyPartContentType><bodyPartIndex>1</bodyPartIndex><errorThreshold>10</errorThreshold><pollingInterval>5</pollingInterval><pollingUnitOfMeasure>Minutes</pollingUnitOfMeasure><uri>POP3://test.microsoft.com#testuser</uri></Config></AdapterConfig></CustomProps>  
```  
  
> [!NOTE]
>  When specifying TransportTypeData configuration data for an adapter that is built using the Adapter Framework, the name/value pairs that are used must all be stored into the \<AdapterConfig> element. Since the \<AdapterConfig> element specifies the VT_BSTR (vt="8") data type then the \< > characters in the data must be escaped.