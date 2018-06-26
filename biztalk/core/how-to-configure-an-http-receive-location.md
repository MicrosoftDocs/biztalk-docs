---
title: "How to Configure an HTTP Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive locations, HTTP adapters"
  - "configuring [HTTP adapters], receive locations"
  - "HTTP adapters, receive locations"
ms.assetid: 901adfc8-0361-49d9-b992-c27089dfbd3b
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure an HTTP Receive Location
You can set HTTP receive location adapter variables either programmatically or by using the BizTalk Server Administration console. If properties are not set in the receive location, the default receive handler values set in the BizTalk Server Administration console are used.  

> [!NOTE]
>  Before completing the following procedure you must have already added a receive port. For more information see, [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).  

 **How to Configure an HTTP Receive Location Programmatically**  

 The HTTP adapter stores its configuration information in the BizTalk Management database (also known as the Configuration database). The configuration is stored in a custom XML property bag.  

 The BizTalk Explorer object model exposes the **IReceiveLocation** configuration interface, which has a **TransportTypeData** read/write property. This property accepts the HTTP receive location configuration property bag in a name-value pair XML string.  

 Setting the **TransportTypeData** property of the **IReceiveLocation** is not required. If it is not set, the default values for the HTTP receive location configuration are used. The following table lists the default values, and also lists the configuration properties that you can set in the BizTalk Explorer object model for the HTTP receive location.  

|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|**ResponseContentType**|string|Content type of the HTTP response messages that the HTTP adapter sends back to clients from this receive location. This property is valid only for request-response receive ports and is ignored for one-way receive ports.|String<br /><br /> **Minimum length:** 0<br /><br /> **Maximum length:** 256|Default value: Text/XML|  
|**LoopBack**|Boolean|Specifies that the request message received on this location will be routed either to a send port or back to the receive location to be sent as a response. This property is valid only for request-response receive ports. It is ignored for one-way receive ports.|None|**Default value:** False|  
|**ReturnCorrelationHandle**|Boolean|Specifies that the correlation token of submitted message that the HTTP adapter sends on HTTP response to the client if the submission is successful. This property is valid only for one-way receive ports and is ignored for request-response receive ports.|None|**Default value:** True|  
|**SuspendFailedRequests**|Boolean|Specifies whether to suspend failed HTTP requests. A value of True indicates to suspend the failed request and send an "Accepted" status code (202) to the client for one-way receive ports or an "Error" status code (500) to the client for two-way receive ports.|None|**Default value:** False|  
|**UseSSO**|Boolean|Specifies whether the HTTP adapter will issue the SSO ticket to messages that arrive on this receive location.|None|**Default value:** False|  

 The format of the XML string to set these properties is as follows:  

```  
<CustomProps>  
   <UseSSO vt="11">-1</UseSSO>  
   <SuspendFailedRequests vt="11">-1</SuspendFailedRequests>  
   <ReturnCorrelationHandle vt="11">-1</ReturnCorrelationHandle>  
   <ResponseContentType vt="8">text/xml</ResponseContentType>  
   <LoopBack vt="11">-1</LoopBack>  
</CustomProps>  

```  

 **How to Configure an HTTP Receive Location with the BizTalk Server Administration Console**  

 To configure the receive location by using the BizTalk Server Administration console, use the following procedure.  

### To configure variables for an HTTP receive location  

1. Configure Internet Information Services (IIS) to work with HTTP receive locations. For instructions about configuring IIS, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).  

2. In the BizTalk Server Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application in which you want to create a receive location.  

3. In the left pane, click the **Receive Ports** node. Then in the right pane, right-click the receive port that is associated with an existing receive location or that you want to associate with a new receive location, and then click **Properties**.  

4. In the **Receive Port Properties** dialog box, in the left pane, select **Receive Locations**, and in the right pane, double-click an existing receive location or click  **New** to create a new receive location.  

5. In the **Receive Location Properties** dialog box, in the **Transport** section next to **Type**, select **HTTP** from the drop-down list and then click **Configure**.  

6. In the **HTTP Transport Properties** dialog box, do the following:  


   |                           Use this                           |                                                                                                                                                                                                                                                                                                                                To do this                                                                                                                                                                                                                                                                                                                                |
   |--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |          **Virtual directory plus ISAPI extension**          | Specify the name of the virtual directory where you post the messages received by the HTTP/HTTPS receive location. The virtual directory includes the name of the receive location DLL and an optional query string. Examples of virtual directory names are:<br /><br /> /\<virtual directory\>/BTSHTTPReceive.dll<br /><br /> /\<virtual directory\>/BTSHTTPReceive.dll?Purchase%20Order<br /><br /> This location must not contain more than one BTSHTTPReceive.dll ISAPI extension, including all subfolders.<br /><br /> **Type:** String<br /><br /> **Maximum length:** 256 **Note:**  The URI for a send port or receive location cannot exceed 256 characters.  |
   |                      **Public Address**                      | Specify the fully qualified URI for this receive location. The value for this property is a combination of the server name and the virtual directory. The BizTalk Messaging Engine exposes this address to external partners. The specified URI should designate the public Web site URL for trading partners to connect to when sending messages to BizTalk Server.<br /><br /> This information is optional and is not used by BizTalk Server. This parameter is available to allow administrators to document the public URL that the receive location is tied to.<br /><br /> **Type:** String<br /><br /> **Minimum length:** 0<br /><br /> **Maximum length:** 256 |
   |                   **Return Content type**                    |                                                                                                                                                                            Specify the content type of HTTP response messages that the receive location sends back to clients. This property is valid only for request-response receive locations.<br /><br /> **Default value:** text/xml<br /><br /> **Type:** String<br /><br /> **Minimum length:** 0<br /><br /> **Maximum length:** 256                                                                                                                                                                            |
   |                         **Loopback**                         |                                                                                                                                                                                       Define that the request message received on this location is routed either to a send port or back to this receive location to be sent as a response. This property is valid only for request-response receive locations.<br /><br /> **Default value:** False<br /><br /> **Type:** Boolean                                                                                                                                                                                        |
   | **Return correlation handle on success (One way port only)** |                                                                                                                                                                                                  Define that if successful, the receive location sends the correlation token of the submitted message on the HTTP response to the client. This property is valid only for one-way receive locations.<br /><br /> **Default value:** True<br /><br /> **Type:** Boolean                                                                                                                                                                                                   |
   |                    **Use Single Sign On**                    |                                   Indicate that Enterprise Single Sign-On is used.<br /><br /> **Default value:** False<br /><br /> **Type:** Boolean **Note:**  If this option is enabled then you must also enable the option to **Allow Tickets** at the **SSO System** level. The **Allow Tickets** option is configurable on the **Options** tab of the **SSO System Properties** dialog box available in the **SSO Administration** MMC interface. If this option is enabled and the **Allow Tickets** option at the **SSO System** level is not enabled then any messages received by this receive location will be suspended.                                    |
   |                 **Suspend Failed Requests**                  |                                                                              Indicate whether or not to suspend HTTP requests that fail inbound processing.<br /><br /> A value of False indicates to discard the failed request and send an error status code (401 or 500) to the client.<br /><br /> A value of True indicates to suspend the failed request and send an "Accepted" status code (200) to the client for one-way receive ports or an "Error" status code (500) to the client for two-way receive ports.<br /><br /> **Default value:** False<br /><br /> **Type:** Boolean                                                                              |


7. Click **OK** to save settings.  

8. Enter the appropriate values in the **Receive Location Properties** dialog box to complete the configuration of the receive location and click **OK** to save settings. For information about the **Receive Locations Properties** dialog box, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  

   While the HTTP client calls the HTTP Location, the HTTP adapter authenticates the HTTP client by using either Anonymous, Basic, Digest, or Windows Integrated authentication. If the user is verified, the user context is passed to the receive handler.  

> [!NOTE]
>  Any IIS configuration that leads to SOAP and HTTP sharing the same process is not valid. You can have only one isolated receiver per process.