---
title: "Receive Location Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.receivelocation.properties"
ms.assetid: a51afe52-a9a5-40c0-b3ca-51abdf6d7a3f
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Location Properties Dialog Box
Use the **Receive Location Properties** window to configure receive locations and associate them with receive ports and pipelines.  
  
## General Tab  
 Use the **General** tab to associate the receive location with the receive handler of the selected host.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Name**|Type the name of the receive location.|  
|**Receive port**|Displays the name of the parent receive port associated with this receive location. You select the receive port in the **Select a Receive Port** dialog box when you create the receive location.|  
|**Transport - Type**|From the drop-down list, select the transport type, or transport protocol. If you change the transport type, you must change the URI.|  
|**Transport - Configure**|After you select the transport type, click **Configure** to display the **Transport Properties** dialog box and configure adapter properties for the receive location.|  
|**Transport - URI**|Displays the destination address to which messages sent through the port will go. You enter this property in the **Transport Properties** dialog box.|  
|**Transport - Receive handler**|From the drop-down list, select the instance of the BizTalk Server host on which the receive location is running.|  
|**Receive pipeline**|From the drop-down list, select the receive pipeline to use to receive messages at this receive location. **Note:**  If you have recently deployed a custom pipeline to BizTalk Server, you may need to refresh the **Pipelines** folder for the appropriate BizTalk application in order to select the custom pipeline from the drop-down list.  To refresh the **Pipelines** folder, open the BizTalk Administration console, click to expand the BizTalk group, click to expand **Applications**, click to expand the BizTalk application that the pipeline was deployed to, right-click the **Pipelines** folder and then click the **Refresh** button.|  
|**Send pipeline**|From the drop-down list, select the send pipeline to use to send responses from this receive location. This list is available only for a receive location associated with a request-response receive port. **Note:**  If you have recently deployed a custom pipeline to BizTalk Server, you may need to refresh the **Pipelines** folder for the appropriate BizTalk application in order to select the custom pipeline from the drop-down list.  To refresh the **Pipelines** folder, open the BizTalk Administration console, click to expand the BizTalk group, click to expand **Applications**, click to expand the BizTalk application that the pipeline was deployed to, right-click the **Pipelines** folder and then click the **Refresh** button.|  
|**Make this the primary location**|Select this check box if you have more than one receive location for a receive port and you want this receive location to represent the receive port when the port needs to be passed to another entity, such as a business partner, that needs to send messages to your organization. The first receive location created is automatically selected as the primary receive location. This property remains selected and unavailable until you designate a different receive location as the primary.|  
|**Description**|Type a description of the receive location.|  
  
## Schedule Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Start date**|From the pull-down calendar, select the date on which the receive location starts processing messages. To change the year, click the displayed year.|  
|**Stop date**|From the pull-down calendar, select the date on which the receive location stops processing messages. This property is optional. If you do not specify a stop date, the receive location remains active until it is disabled.|  
|**Service Window - Enable service window**|Select this check box to configure the receive location to receive messages only at specified times of the day, then specify the times in the **Start time and Stop time** boxes. If the check box is cleared, the receive location receives messages at any time. The default value is false (cleared).|  
|**Service Window - Start time**|Specify the time when the receive location should begin to receive messages. This box is available only when the **Enable service window** check box is selected.|  
|**Service Window - Stop time**|Specify the time when the receive location should cease to receive messages. This box is available only when the **Enable service window** check box is selected.|  
  
## Certificate Tab  
 The **Certificate** tab appears only for request-response receive locations.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Encryption certificate - Description**|Displays a description of the selected encryption certificate.|  
|**Encryption certificate - Thumbprint**|Displays the thumbprint of the public key certificate used to encrypt outbound messages. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit.|  
|**Encryption certificate - Remove certificate**|Click to remove the selected certificate.|  
|**Encryption certificate - Browse**|Click to display the **Select Certificate** dialog box, where you select the encryption certificate from the Local Machine or Other People certificate store to use for this receive location.|  
  
## See Also  
 [Receive Locations](../core/receive-locations.md)   
 [How to Configure a Windows SharePoint Services Receive Location](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)   
 [How to Configure Scheduling for a Receive Location](../core/how-to-configure-scheduling-for-a-receive-location.md)   
 [How to Enable a Receive Location](../core/how-to-enable-a-receive-location.md)   
 [Minimum Security User Rights](../core/minimum-security-user-rights.md)