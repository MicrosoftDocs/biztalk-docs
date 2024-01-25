---
description: "Learn more about: The ESB JMS Encoder and Decoder Components"
title: "The ESB JMS Encoder and Decoder Components"
ms.custom: "devx-track-javaee-websphere"
ms.date: "12/30/2022"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The ESB JMS Encoder and Decoder Components
Some integration solutions involve Java Message Service (JMS) and SOAP messages sent to or from IBM WebSphere MQ; [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes two JMS pipeline components written in managed code for use in these situations. The components read or write the JMS portion of the MQ message header using the values of context properties associated with the message. Currently, there are more than 60 different types of JMS headers in use with WebSphere MQ Series systems; the ESB JMS components work only with MQRFH2 headers.  
  
## Installation  
 Installing the ESB Core automatically installs the JMS Encoder and JMS Decoder components in the BizTalk Server Pipeline Components folder.  
  
## How It Works  
 The JMS pipeline components inspect the message headers and operate only on messages that have the **MQMD_Format** header set to **RFH (MQRFH2)**. However, even when this property is set, the components inspect the headers to confirm that they do conform to the IBM RFH2 format. If the header does not conform to this format, the components generate a parse error that indicates the **MQMD_Format** parameter was set to **RFH (MQRFH2)**, but the structure of the header did not comply with the RFH2 standard. If inbound message header parsing fails, the decoder component allows the message to pass, but it sets a message context property named **MQRFH2_ParseError** to **True**.  
  
 The **MQRFH2** property schema deployed in BizTalk with the JMS components exposes all of the MQRFH2 header properties. After demoting the headers of an incoming message, the data from the headers resides in an XML document stored in the **MQRFH2_NameValueData** context property of the message. The encoder adjusts the length of the **NameValueData** folder to ensure it is the correct length. To understand the usage of these headers, and the impact when changing the values, review the appropriate IBM documentation.  
  
## Using the JMS Encoder and Decoder Components  
 To use the JMS Encoder and Decoder components, developers add them to pipelines in a BizTalk application. For a send pipeline, the JMS Encoder component should reside in the Encode stage. For a receive pipeline, the JMS Decoder component should reside in the Decode stage. The JMS components will not install in any other stages of a pipeline.  
  
 When installed in the Encode stage, the JMS Encoder component reads the values in the JMS **MQRFH2** headers and writes (promotes) them into the message context properties. When installed in the Decode stage, the JMS Decoder component reads (demotes) the context property values and inserts them into the JMS **MQRFH2** headers. This means that all the MQ header values are available as context properties of the message in the pipeline.  
  
 To detect and manage header-parsing errors, developers can include code that examines the value of the **MQRFH2_ParseError** property. They can implement a recovery process that subscribes to failed messages or specify send ports that filter on the **MQRFH2_ParseError** property to persist the message. Subscribers that work with JMS messages should include a filter condition that specifies the value **False** for the **MQRFH2_ParseError** property to prevent the subscriber from receiving messages that failed the header parsing process.  
  
 Developers can also update the context property values (for example, change the **MQRFH2_Encoding** property value), and the component will reflect these changes in the MQ message headers so that they are set when the message arrives at its ultimate destination. The component automatically ignores invalid values and sets "safe" default values where required headers are missing. For example, if the developer specifies an invalid value for the **MQRFH2_Encoding** property, the outbound message will have the **MQRFH2_Encoding** header set to **UNKNOWN**. If the developer removes a value from a context property, but the **MQMD_Format** property is still set to **RFH**, the component will add a header containing the default value, as per the IBM specification.  
  
 For an example of how to use these components, see [Installing and Running the JMS MQRFH2 Component Sample](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md).
