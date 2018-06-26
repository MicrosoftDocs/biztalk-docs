---
title: "How to Configure an SMTP Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [SMTP adapters], send ports"
  - "send ports, SMTP adapters"
  - "SMTP adapters, send ports"
ms.assetid: b2291378-718d-4d1a-9d54-cd34c1b2e000
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure an SMTP Send Port
You can configure an SMTP send port either programmatically or by using the BizTalk Server Administration console.  
  
 **How to Configure an SMTP Send Port Programmatically**  
  
 The SMTP adapter stores its configuration information in the BizTalk Management database (also known as the Configuration database). Configuration information is stored in a custom XML property bag. During initialization of the SMTP adapter and during its run time, the server passes the configuration to the adapter as follows:  
  
- For the SMTP send handler, configuration information passes to the adapter by calling the **Load** method of the **IPersistPropertyBag** interface.  
  
- For the SMTP send adapters, configuration information passes to the adapter as a set of properties on a message context. The SMTP namespace groups these properties together.  
  
  The BizTalk Explorer object model exposes the ITransportInfo adapter configuration interface for send ports, which contains the TransportTypeData read/write property. This property accepts the SMTP send port configuration property bag as a name/value pair XML string. Note that to set this property in the BizTalk Explorer object model, it must first be set on the Address property of the **ITransportInfo** interface.  
  
  Setting the **TransportTypeData** property of the **ITransportInfo** interface is not required. If it is not set, the SMTP send port uses the default values for the SMTP send handler. SMTP send port-specific properties are defined in SMTP send adapter property schema bts_smtp_properties.xsd.  
  
  If you do not define properties that duplicate the send handler configuration properties, configuration properties for the handler are used. If you do not define required properties, default values are used. If you do not define default values, the SMTP send handler logs an error in the event log and moves the message to the backup adapter.  
  
  You can set these properties programmatically on a message context. You can set these properties in a BizTalk orchestration schedule or in a custom pipeline component. The following rules apply when using these properties:  
  
- If the property is set in an orchestration or in a custom pipeline component in a receive pipeline, then:  
  
  -   If the message is sent to a static send port, the property value will be overwritten with the value configured for that send port.  
  
  -   If the message is sent to a dynamic send port, the property value will not be overwritten.  
  
- If the property is set in a custom pipeline component in a send pipeline, then:  
  
  -   The value will not be overwritten regardless of whether the message is sent to a static or dynamic send port.  
  
  The following table lists the configuration properties that you can set in the BizTalk Explorer object model for the SMTP send location.  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|**SMTPHost**|xs:string|SMTP server used to send messages.|Maximum length: 256|Default value: Empty.<br /><br /> The default value indicates that the SMTP send port will use the configuration values for the handler.|  
|**From**|xs:string|The e-mail address that the SMTP send port places on the SMTP **From** header.|Maximum length: 256|Default value: Empty.<br /><br /> The default value indicates that the SMTP send port will use the configuration values for the handler.|  
|**CC**|xs:string|E-mail address where a copy of the message will be sent.|Maximum length: 1024|Default value: Empty<br /><br /> You can list several e-mail addresses.|  
|**Subject**|xs:string|Subject header for the messages.|Minimum length: 0<br /><br /> Maximum length: 256|Default value:  %MessageID%.|  
|**SMTPAuthenticate**|xs:int|Type of authentication to use.|None|Valid values:<br /><br /> -   0 - No authentication<br />-   1- Basic authentication<br />-   2 - Process account (NTLM)<br /><br /> The default value indicates that the SMTP send port will use the configuration values for the handler. To apply the default value, omit this property from the property bag when setting the TransportTypeData property.|  
|**UserName**|xs:string|User name to use for authentication with the SMTP server.|Minimum length: 0<br /><br /> Maximum length: 256|Default value: Empty<br /><br /> Requires a value if **SMTPAuthenticate** is equal to 1 (Basic authentication).|  
|**Password**|xs:string|User password for authentication with the SMTP server.|Minimum length: 0<br /><br /> Maximum length: 256|Default value: Empty<br /><br /> Requires a value if **SMTPAuthenticate** is equal to 1 (Basic authentication).|  
|**ReadReceipt**|xs:boolean|Requests a read receipt for the messages from this send port.|None|Default value: False|  
|**DeliveryReceipt**|xs:boolean|Requests a delivery receipt for the messages from this send port.|None|Default value: False|  
|**EmailBodyText**|xs:string|Specify text to be used for the body of the e-mail being sent.|Maximum length: 64 kb|Default value: Empty|  
|**EmailBodyTextCharset**|xs:string|Specify the character set to use for encoding the body of the e-mail being sent when the **EmailBodyText** option is used. The SMTP adapter will convert the **EmailBodyText** to the character set specified by **EmailBodyTextCharset**.|None|Default value: None. You must explicitly set the value, for example, to UTF-8.<br /><br /> If you don't set a value, you may see the error shown at the end of this topic.|  
|**EmailBodyFile**|xs:string|Specifies that the contents of a file will be used for the body of the e-mail being sent and the full path to the file. This path must be accessible to the host for the SMTP adapter at run time.|Maximum path length: 256 characters|Default value: Empty|  
|**EmailBodyFileCharset**|xs:string|Specify the character set to use for encoding the body of the e-mail being sent if the **EmailBodyFile** property is set. The SMTP adapter will not perform any conversion on the file; the file must already be encoded in this character set. If the file has a Byte-Order-Mark (BOM), the SMTP adapter will remove it.|None|Default value: UTF-8 (65001)|  
|**Attachments**|xs:string|Specifies that a file or files will be attached to the e-mail message and the full path to the file or files. The specified path or paths must be accessible to the host for the SMTP adapter at run time.|Maximum path length: 256 characters|Default value: Empty|  
|**MessagePartsAttachments**|xs:int|Specify how BizTalk message parts are attached to the e-mail message|None|Valid values:<br /><br /> -   0 - No BizTalk message parts will be used as attachments.<br />-   1- The BizTalk message body part is sent as an e-mail attachment. In this case, the **EmailBodyFile** or **EmailBodyText** properties should be specified. If neither of these properties are specified, the BizTalk message body part is sent as the e-mail body instead of as an attachment.<br />-   2 - All parts are sent as attachments. However, if **EmailBodyText** or **EmailBodyFile** are not specified, then the BizTalk message body part is sent as the e-mail body and other parts are sent as attachments.<br /><br /> Default value: 0|  
|**ReplyBy**|xs:dateTime|Populates the **Reply-By** header field in the outgoing message with the specified value.|This property cannot be set on the send port property page. This property can be set from a pipeline or an orchestration.|Default value: Empty|  
  
 The following code shows the format of the XML string to use to set these properties:  
  
```  
<CustomProps>  
   <DeliveryReceipt vt="11">-1</DeliveryReceipt  
   <SMTPHost vt="8">sfdsadf</SMTPHost>  
   <Subject vt="8">Some subject</Subject>  
   <From vt="8">username@domain.com</From>  
   <SMTPAuthenticate vt="19">2</SMTPAuthenticate>  
   <ReadReceipt vt="11">-1</ReadReceipt>  
</CustomProps>  
```  
  
 **How to Configure an SMTP Send Port with the BizTalk Server Administration Console**  
  
 You can set SMTP send port adapter variables in the BizTalk Server Administration Console. If properties are not set for the send port, the default send handler values set in the BizTalk Server Administration Console are used.  
  
 To configure an SMTP send port with the BizTalk Server Administration console, use the following procedure.  
  
### To configure variables for an SMTP send port  
  
1.  In the BizTalk Server Administration Console, create a new send port or double-click an existing send port to modify it. For more information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md). Configure all of the send port options and specify **SMTP** for the **Type** option in the **Transport** section of the **General** tab.  
  
2.  On the **General** tab, in the **Transport** section, next to **Type**, click **Configure**.  
  
3.  In the **SMTP Transport Properties** dialog box, on the **General** tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**To**|Required. Specify the e-mail address for where to send messages.<br /><br /> You can specify more than one address.<br /><br /> Maximum length: 256<br /><br /> For more information about this property, see [Restrictions on the SMTP To Property](../core/restrictions-on-the-smtp-to-property.md).|  
    |**CC**|Specify the e-mail address to send the carbon copy of the message.<br /><br /> You can specify more than one address.<br /><br /> Maximum length: 1024|  
    |**Subject**|Specify the subject header for the message.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
    |**Notification**|Specify the type of notification receipt. You can select one or both types of receipts. Notification receipt types are:<br /><br /> -   **Read Receipt**. Confirmation e-mail message is sent when the message is read.<br />-   **Delivery Receipt**. Confirmation e-mail message is sent when the message is delivered.|  
  
4.  In the **SMTP Transport Properties** dialog box, on the **Compose** tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**BizTalk message body part**|Specify to use the BizTalk message body part for the body of the e-mail being sent.|  
    |**Text**|Specify text to be used for the body of the e-mail being sent. After the **Text** option is selected you can enter the text for the e-mail body into the text box.<br /><br /> **Maximum Length:** 64Kb|  
    |**Charset for the text**|-   Specify the character set to use for encoding the body of the e-mail being sent. This option is only available if the **Text** option is selected.<br />-   **Default value:** UTF-8 (65001)|  
    |**File**|Specify that the contents of a file will be used for the body of the e-mail being sent and specify the path to the file. After the **File** option is selected you can click the Ellipsis (**…**) button to browse to the file.<br /><br /> Maximum path length: 256 characters **Note:**  It is a recommended best practice to specify a path on a file share that is accessible from all BizTalk servers in the BizTalk Server group to be used in production.|  
    |**Charset of the file**|Specify the character set encoding of the file being sent. **Note:**  The SMTP adapter does not apply the specified encoding to the file. This option is only for specifying how the file being sent is already encoded. <br /><br /> This option is only available if the **File** option is selected.<br /><br /> Default value: UTF-8 (65001)|  
  
5.  In the **SMTP Transport Properties** dialog box, on the **Attachments** tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Remaining BizTalk message parts**|Specify how BizTalk message parts are attached to the e-mail message.<br /><br /> Options:<br /><br /> -   **Do not attach parts**<br />-   **Attach only body part**<br />-   **Attach all parts**<br /><br /> Default value: Do not attach parts.|  
    |**Add**|Specify a file or files to attach to the e-mail message. After clicking **Add** you can browse to select a file and add it to the list of files to be attached.<br /><br /> Maximum path length: 256 characters **Note:**  It is a recommended best practice to specify a path on a file share that is accessible from all BizTalk servers in the BizTalk Server group to be used in production.|  
    |**Remove**|Removes the selected file from the list of files to be attached to the e-mail message.|  
  
6.  In the **SMTP Transport Properties** dialog box, on the **Handler Override** tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**SMTP server name**|Specify the name of the SMTP server to use when sending messages.<br /><br /> Maximum length: 256 **Note:**  The URI for a send port or receive location cannot exceed 256 characters.|  
    |**From (e-mail address)**|Specify the e-mail address to place on the SMTP **From** header.<br /><br /> Maximum length: 256|  
    |**Authentication type**|Specify the type of authentication to use with the SMTP server.<br /><br /> Options:<br /><br /> -   **(Default)**<br />-   **No authentication**<br />-   **Basic authentication**<br />-   **Process account (NTLM)**<br /><br /> The default value indicates that the SMTP send port will use the configuration values specified in the send handler.|  
    |**User name**|Specify the user name to use for authentication with the SMTP server.<br /><br /> This property requires a value if **Authentication type** is **Basic authentication**.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
    |**Password**|Specify the password to use for authentication with the SMTP server.<br /><br /> This property requires a value if **Authentication type** is **Basic authentication**.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
  
7.  Click **OK** and **OK** again to save settings.  
  
## See Also  
 [Configuring the SMTP Adapter](../core/configuring-the-smtp-adapter.md)