---
description: "Learn more about: Affiliate Applications Properties: Options"
title: "Affiliate Applications Properties: Options2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Affiliate Applications Properties: Options
Use this dialog box to view or change options for the Affiliate Application.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Enabled**|The status (enabled/disabled) of this affiliate application.|  
|**Allow Windows initiated SSO**|Select if Windows initiated Enterprise Single Sign-On (SSO) is allowed.|  
|**Disable credential cache**|The SSO Server stores credentials in a cache to expedite access. Default is not checked.|  
|**Tickets allowed**|Determines whether the SSO system uses tickets for this affiliate application. You must be an SSO administrator to select this option.|  
|**Validate tickets**|Determines whether the SSO system validates tickets when the user redeems them. You must be an SSO administrator to select this option.|  
|**Timeout tickets**|Determines whether tickets have an expiration time. Default is checked. Unless it is required, do not disable ticket timeouts. You must be an SSO administrator to set this option.|  
|**Ticket timeout (in minutes)**|Specifies a ticket timeout specific to the affiliate application. This can be set only when updating an affiliate application, not when creating it. If ticketing is enabled for this application and this property is not, the timeout specified at the SSO System (Global) level is used. You must be an SSO administrator to set this option.|  
|**Allow host initiated SSO**|Select this if it is a host initiated SSO type application. Default is not checked.|  
|**Verify external credentials**|Select to verify external credentials.|  
  
## See Also  
 [Enterprise Single Sign-On (Configuration)](../core/enterprise-single-sign-on-configuration-1.md)   
 [Affiliate Applications Properties](../core/affiliate-applications-properties2.md)
