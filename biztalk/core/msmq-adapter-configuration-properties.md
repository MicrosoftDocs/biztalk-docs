---
description: "Learn more about: MSMQ Adapter Configuration Properties"
title: "MSMQ Adapter Configuration Properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MSMQ Adapter Configuration Properties
The following table lists the configuration properties that you can set for an MSMQ adapter receive location:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|queue|VT_BSTR|Specify a valid queue path to the location monitored by the receive location.|The URI for a send port or receive location cannot exceed 256 characters.|None|  
|batchSize|VT_BSTR|Specify the batch size that the MSMQ adapter uses when submitting a batch of messages to the MessageBox database.|Valid values are from 1 to 4294967295.|The default value is 20.|  
|transactional|VT_BSTR|Specify whether to read messages from the source queue under the context of a Microsoft Distributed Transaction (MSDTC).|Valid values are:<br /><br /> -   true<br />-   false<br /><br /> The adapter does not support transactional reads on remote queues.|The default value is false.|  
|serialProcessing|VT_BSTR|Specify whether to process messages in order.|Valid values are:<br /><br /> -   true<br />-   false|The default value is false.|  
|onFailure|VT_BSTR|Specify how the adapter should respond to an error.|Valid values are:<br /><br /> -   stopOnFailure<br />-   suspendNonResumable<br />-   suspendResumable|The default value is suspendResumable.|  
|uri|VT_BSTR|Specify the full path to the queue monitored by the receive location.|The URI for a send port or receive location cannot exceed 256 characters.|None|  
  
 The following code shows the format of the string you use to set the properties:  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><queue>FORMATNAME:DIRECT=OS:.\PRIVATE$\QUEUE</queue><batchSize>20</batchSize><transactional>false</transactional><serialProcessing>false</serialProcessing><onFailure>suspendResumable</onFailure><uri>FORMATNAME:DIRECT=OS:.\PRIVATE$\QUEUE</uri></Config></AdapterConfig></CustomProps>  
```  
  
 The following table lists the configuration properties that you can set for an MSMQ adapter send port:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|Queue|VT_BSTR|Specify the destination queue.|The URI for a send port or receive location cannot exceed 256 characters.|None|  
|maximumMessageSiz|VT_BSTR|Specify the maximum message size in kilobytes (KB) for messages that you send to the specified queue.|Valid values are from 1 to 4294967295 if segmentationSupport and transactional are set to true. Otherwise, valid values are from 1 to 4095.|The default value is 1024.|  
|acknowledgeType|VT_BSTR|Specify one or more acknowledgement types.|Valid values are the members of the .NET **System.Messaging.AcknowledgeTypes** enumeration.|The default value is None.|  
|administrationQueue|VT_BSTR|Specify the MSMQ administration queue.|None|None|  
|timeOut|VT_BSTR|Specify the maximum time to wait for the messages to reach the destination queue.|This property only applies when the transactional property is set to true.<br /><br /> -   Valid values are 1 to 10675199 when specifying a timeOutUnits value of Days.<br />-   Valid values are 1 to 596523 when specifying a timeOutUnits value of Hours.<br />-   Valid values are 1 to 35791394 when specifying a timeOutUnits value of Minutes.<br />-   Valid values are 1 to 2147483647 when specifying a timeOutUnits value of Seconds.|None|  
|priority|VT_BSTR|Specify the message priority.|Valid values are the members of the .NET **System.Messaging.MessagePriority** enumeration.|None|  
|recoverable|VT_BSTR|Specify whether to guarantee the recoverability of a message.|Valid values are:<br /><br /> -   true<br />-   false|The default value is false.|  
|encryptionAlgorithm|VT_BSTR|Specify the encryption algorithm to be used.|Valid values are the members of the .NET **System.Messaging.EncryptionAlgorithm** enumeration.|The default value is None.|  
|useAuthentication|VT_BSTR|Specify whether to use authentication.|Use this property in combination with the certificate property to verify the message. Use the userName and password properties to gain access to queues.|None|  
|certificate|VT_BSTR|Specify the certificate used to verify messages.|Enter the 40 character certificate thumbprint.|None|  
|segmentationSupport|VT_BSTR|Specify whether segmentation is supported.|Valid values are:<br /><br /> -   true<br />-   false|The default value is false.|  
|transactional|VT_BSTR|Specify whether to support sending messages under the context of a Microsoft Distributed Transaction (MSDTC)|Valid values are:<br /><br /> -   true<br />-   false|The default value is false.|  
|useJournalQueue|VT_BSTR|Specify whether to save a copy of the message whenever the message is processed.|Valid values are:<br /><br /> -   true<br />-   false|The default value is false.|  
|useDeadLetterQueue|VT_BSTR|Specify whether to send messages to the dead letter queue if a failure occurs.|Valid values are:<br /><br /> -   true<br />-   false|The default value is true.|  
|ackTypeEnumsValue|VT_BSTR|Specify the bitwise OR of the values associated with the specified acknowledgeType values.|None|The default value is 0.|  
|timeOutUnits|VT_BSTR|Specify the unit to use in conjunction with the value specified for the timeOut property.|Valid values are:<br /><br /> -   Days<br />-   Hours<br />-   Minutes<br />-   Seconds|The default value is Days.|  
|userName|VT_BSTR|Specify the user name for a remote queue.|The default value is empty.|  
|password|VT_BSTR|Specify the password to be used in conjunction with the value specified for the userName property for access to a remote queue.|This value is always masked when exporting a binding file. This field must be manually populated with the password before importing the binding file into the target BizTalk Server configuration.|The default value is empty.|  
|bodyType|VT_BSTR|Specify the message body type in MSMQ.|Valid values are members of the .NET **VarEnum** enumeration.|The default value is 8209.|  
|uri|VT_BSTR|Specify the full path to the destination queue.|The URI for a send port or receive location cannot exceed 256 characters.|None|  
  
 The following code shows the format of the string you use to set the properties:  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><queue>FORMATNAME:DIRECT=OS:TESTSERVER\PRIVATE$\DESTQUEUE</queue><maximumMessageSize>1024</maximumMessageSize><acknowledgeType>None</acknowledgeType><administrationQueue>Direct=OS:TestServer\Private$\AdminQueue</administrationQueue><timeOut>4</timeOut><priority>Normal</priority><recoverable>false</recoverable><encryptionAlgorithm>None</encryptionAlgorithm><useAuthentication>false</useAuthentication><segmentationSupport>false</segmentationSupport><transactional>false</transactional><useJournalQueue>false</useJournalQueue><useDeadLetterQueue>true</useDeadLetterQueue><ackTypeEnumsValue>0</ackTypeEnumsValue><timeOutUnits>Days</timeOutUnits><userName>TestUser</userName><password>******</password><bodyType>8209</bodyType><uri>FORMATNAME:DIRECT=OS:TESTSERVER\PRIVATE$\DESTQUEUE</uri></Config></AdapterConfig>  
```  
  
> [!NOTE]
>  When specifying TransportTypeData configuration data for an adapter that is built using the Adapter Framework, the name/value pairs that are used must all be stored into the \<AdapterConfig\> element. Since the \<AdapterConfig\> element specifies the VT_BSTR (vt="8") data type then the \< \> characters in the data must be escaped.
