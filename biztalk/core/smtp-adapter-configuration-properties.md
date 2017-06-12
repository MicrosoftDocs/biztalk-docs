---
title: "SMTP Adapter Configuration Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SMTP adapters, properties"
  - "SMTP adapters, code sample"
  - "SMTP adapters, send ports"
  - "send ports, adapters"
ms.assetid: 6af287f5-272a-42d7-9878-99a4157c06ce
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SMTP Adapter Configuration Properties
The following table lists the configuration properties that you can set for an SMTP adapter send port:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|DeliveryReceipt|VT_BOOL|Specify that a confirmation e-mail message should be sent when the message is delivered.|Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is 0 (false).|  
|From|VT_BSTR|Specify the e-mail address to place on the SMTP From header.|Minimum length: 0<br /><br /> Maximum length: 256|None|  
|MessagePartsAttachments|VT_UI4|Specify how BizTalk message parts are attached to the e-mail message.|Valid values are:<br /><br /> -   0 (Do not attach message parts)<br />-   1 (Attach only body part<br />-   2 (Attach all parts)|The default value is 0 (Do not attach message parts).|  
|CC|VT_BSTR|Specify the e-mail address to send the carbon copy of the message.|Maximum length: 1024|You can specify more than one address.|  
|SMTPAuthenticate|VT_UI4|Valid values are:<br /><br /> -   0 (Do not authenticate)<br />-   1 (Basic authentication)<br />-   2 (Process account (NTLM))|If this value is not specified then the (Default) value is applied.|The (Default) value indicates that the SMTP send port will use the configuration values specified in the send handler.|  
|Username|VT_BSTR|Specify the user name to use for authentication with the SMTP server.|This property does not require a value unless the SMTPAuthenticate property is set to 1 (Basic authentication).<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|None|  
|EmailBodyFileCharset|VT_BSTR|Specify the character set encoding of the file being sent.|This property does not require a value unless the EmailBodyFile property is set.|The SMTP adapter does not apply the specified encoding to the file, this option is only for specifying how the file being sent is already encoded.<br /><br /> The default value is utf-8.|  
|EmailBodyText|VT_BSTR|Specify text to be used for the body of the e-mail being sent.|Maximum Length: 64Kb|None|  
|ReadReceipt|VT_BOOL|Specify that a confirmation e-mail message should be sent when the message is read.|Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is 0 (false).|  
|To|VT_BSTR|Specify the e-mail address for where to send messages.|None|None|  
|EmailBodyFile|VT_BSTR|Specify the path to the file that is to be used for the body of the e-mail being sent.|Maximum path length: 256 characters|It is a recommended best practice to specify a path on a file share that is accessible from all BizTalk Servers in the BizTalk Server group to be used in production.|  
|Subject|VT_BSTR|Specify the subject header for the message.|Minimum length: 0<br /><br /> Maximum length: 256|None|  
|Password|VT_NULL|Specify the password to use for authentication with the SMTP server.|This property does not require a value unless the SMTPAuthenticate  property is set to 1 (Basic authentication).<br /><br /> This value is always set to null when exporting a binding file. This field must be manually populated with the password before importing the binding file into the target BizTalk Server configuration.|None|  
|Attachments|VT_BSTR|Specify the path to a file that is to be attached to the e-mail being sent.|Maximum path length: 256 characters|None|  
|SMTPHost|VT_BSTR|Specify the name of the SMTP server to use when sending messages.|The URI for a send port or receive location cannot exceed 256 characters.<br /><br /> Maximum path length: 256 characters|None|  
|EmailBodyTextCharset|VT_BSTR|Specify the character set to use for encoding the body of the e-mail being sent.|This property does not require a value unless the EmailBodyText property is set.|The default value is utf-8.|  
  
 The following code shows the format of the XML string you use to set the properties:  
  
```  
<CustomProps>  
<DeliveryReceipt vt="11">-1</DeliveryReceipt>  
<From vt="8">someone@microsoft.com</From>  
<MessagePartsAttachments vt="19">0</MessagePartsAttachments>  
<CC vt="8">someoneelse@microsoft.com</CC>  
<SMTPAuthenticate vt="19">1</SMTPAuthenticate>  
<Username vt="8">OverrideUsername</Username>  
<EmailBodyFileCharset vt="8">utf-8</EmailBodyFileCharset>  
<EmailBodyText vt="8">Email Body Text</EmailBodyText>  
<ReadReceipt vt="11">-1</ReadReceipt>  
<To vt="8">recipient@microsoft.com</To>  
<EmailBodyFile vt="8">C:\emailbodyfile.xml</EmailBodyFile>  
<Subject vt="8">test mail</Subject>  
<Password vt="1" />  
<Attachments vt="8">C:\attachment.txt</Attachments>  
<SMTPHost vt="8">emailhost</SMTPHost>  
<EmailBodyTextCharset vt="8">utf-8</EmailBodyTextCharset>  
</CustomProps>  
```