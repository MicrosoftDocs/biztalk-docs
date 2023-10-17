---
description: "Learn more about: MQSeries Adapter Configuration Properties"
title: "MQSeries Adapter Configuration Properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MQSeries Adapter Configuration Properties
The following table lists the configuration properties that you can set for an MQSeries adapter receive location:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|uri|VT_BSTR|Specify the full path to the location monitored by the receive location.|The URI for a send port or receive location cannot exceed 256 characters.|None|  
|queueDetails|VT_BSTR|Specify information about the source MQSeries queue including server, queue manager, and queue.|-   None|This property is prepended with MQS:// to create the uri property.|  
|transactionSupported|VT_BSTR|Specify whether the MQSeries adapter initiates a Microsoft Distributed Transaction Coordinator (DTC) transaction between BizTalk Server and MQSeries Server.|Valid values are:<br /><br /> -   yes<br />-   no|When set to no, there is no guarantee of message delivery.<br /><br /> The default value is yes.|  
|suspendAsNonResumable|VT_BSTR|Specify whether suspended messages are marked as resumable or not.|Valid values are:<br /><br /> -   yes<br />-   no|The default value is no.|  
|dataOffsetForHeaders|VT_BSTR|The adapter uses values from the MQSeries headers (the MQXQH, MQIIH, and MQCIH structures) to populate corresponding values in the BizTalk Server context properties. By default, the adapter removes these MQSeries properties from the message body.|Valid values are:<br /><br /> -   yes<br />-   no|Set this property to no to retain the properties in the message body.<br /><br /> The default value is yes.|  
|pollingInterval|VT_BSTR|Specify the interval used by the receive component to poll the MQSeries queue.|Valid values are from 1 to 10000.|The pollingInterval works in combination with the hard-coded wait interval of three seconds built in to the adapter. If the pollingInterval value is less than three (3) seconds, the wait interval is set to the value of the pollingInterval.<br /><br /> The default value is 3.|  
|pollingUnit|VT_BSTR|Specify the unit of time for the polling interval.|Valid values are:<br /><br /> -   hours<br />-   minutes<br />-   seconds|The default value is seconds.|  
|maximumBatchSize|VT_BSTR|Specify the maximum size of a batch of messages in kilobytes (KB).|Valid values are from 1 to 10485760|The default value is 100.|  
|maximumNumberOfMessages|VT_BSTR|Specify the maximum number of messages in a batch.|Valid values are from 1 to 100000|The default value is 100.|  
|threadCount|VT_BSTR|Specify the number of threads used per receive location.|Valid values are from 1 to 64.|The default value is 2.|  
|fragmentationSize|VT_BSTR|Specify the message chunk size in kilobytes (KB) for messages as they are sent between MQSAgent and the adapter.|Valid values are from 1 to 1048576.|The default value is 500.|  
|characterSet|VT_BSTR|Specify the character set and whether MQSeries converts characters before sending the message to the receive location.|Valid values are:<br /><br /> -   none. Do not convert.<br />-   UCS-2 and UTF-16. Convert to these character sets. MQSeries does not distinguish between them.<br />-   UTF-8. Convert to the UTF-8 character set.|The default value is none.|  
|errorThreshold|VT_BSTR|Specify the maximum number of errors to log. The adapter continues operating and, if the adapter recovers, it logs the event in the event log.|Valid values are from 1 to 1000.|The default value is 10.|  
|segmentation|VT_BSTR|Specify whether MQSeries assembles segmented messages or gets messages as is.|Valid values are:<br /><br /> -   none<br />-   complete|Specify none to read messages from the MQSeries queue without enabling segmentation.<br /><br /> Specify complete to have MQSeries assemble segmented messages before passing them on to the adapter.<br /><br /> The default value is none.|  
|ordered|VT_BSTR|Specify whether MQSeries maintains the order of the messages as they are received from the MQSeries queue.|Valid values are:<br /><br /> -   no<br />-   noStop<br />-   yesStop<br />-   yesSuspend|Specify no to disregard message order.<br /><br /> Specify noStop to disregard message order and to disable the receive location if there is an error.<br /><br /> Specify yesStop to enable ordering. This option ends the transaction and disables the receive location if there is an error.<br /><br /> Specify yesSuspend to enable ordering. This option moves the message to the suspended queue when there is an error. This value does not preserve order when there is an error, but does allow the receive location to continue receiving messages.<br /><br /> The default value is no.|  
  
 The following code shows the format of the string you use to set the properties:  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><uri>MQS://TESTMQServer/DQM1/RQ0</uri><queueDetails>TESTMQServer/DQM1/RQ0</queueDetails><transactionSupported>yes</transactionSupported><suspendAsNonResumable>no</suspendAsNonResumable><dataOffsetForHeaders>yes</dataOffsetForHeaders><pollingInterval>1</pollingInterval><pollingUnit>seconds</pollingUnit><maximumBatchSize>100</maximumBatchSize><maximumNumberOfMessages>100</maximumNumberOfMessages><threadCount>2</threadCount><fragmentationSize>500</fragmentationSize><characterSet>none</characterSet><errorThreshold>10</errorThreshold><segmentation>none</segmentation><ordered>no</ordered></Config></AdapterConfig></CustomProps>  
```  
  
 The following table lists the configuration properties that you can set for an MQSeries adapter send port:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|uri|VT_BSTR|Specify the full path of the location to send data to.|The URI for a send port or receive location cannot exceed 256 characters.|None|  
|queueDetails|VT_BSTR|Specify information about the target MQSeries queue including server, queue manager, and queue.|The URI for a send port or receive location cannot exceed 256 characters.|This property is prepended with MQS:// to create the uri property.|  
|transactionSupported|VT_BSTR|Specify whether the MQSeries adapter initiates a Microsoft Distributed Transaction Coordinator (DTC) transaction between BizTalk Server and MQSeries Server.|Valid values are:<br /><br /> -   yes<br />-   no|When set to no, there is no guarantee of message delivery.<br /><br /> The default value is yes.|  
|dataConversion|VT_BSTR|Specify whether to convert the message to the ANSI code page of MQSeries for Windows server.|Valid values are:<br /><br /> -   yes<br />-   no|The default value is no.|  
|segmentationAllowed|VT_BSTR|Specify whether to use MQSeries Queue Manager segmentation if an individual message exceeds the MQSeries queue maximum message length.|Valid value are:<br /><br /> -   yes<br />-   no|The default value is no.|  
|fragmentationSize|VT_BSTR|Specify the message chunk size in kilobytes (KB) for messages as they are sent between the adapter and MQSAgent.|Valid values are from 1 to 1048576.|The default value is 500.|  
|ordered|VT_BSTR|Specify whether MQSeries maintains the order of messages as they are sent to the MQSeries queue.|Valid values are:<br /><br /> -   yes<br />-   no|The default value is no.|  
  
 The following code shows the format of the string you use to set the properties:  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><uri>MQS://TESTMQServer/DQM1(QM1)/SQ0</uri><queueDetails>TESTMQServer/DQM1(QM1)/SQ0</queueDetails><transactionSupported>yes</transactionSupported><dataConversion>no</dataConversion><segmentationAllowed>no</segmentationAllowed><fragmentationSize>500</fragmentationSize><ordered>no</ordered></Config></AdapterConfig></CustomProps>  
```  
  
> [!NOTE]
>  When specifying TransportTypeData configuration data for an adapter that is built using the Adapter Framework, the name/value pairs that are used must all be stored into the \<AdapterConfig\> element. Since the \<AdapterConfig\> element specifies the VT_BSTR (vt="8") data type then the \< \> characters in the data must be escaped.
