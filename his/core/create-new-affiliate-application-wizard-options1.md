---
description: "Learn more about: Create New Affiliate Application Wizard: Options"
title: "Create New Affiliate Application Wizard: Options1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Create New Affiliate Application Wizard: Options
Specify options for the new Affiliate Application.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Enabled**|The status (enabled/disabled) of this affiliate application.|  
|**Allow Windows initiated SSO**|Select if Windows initiated Enterprise Single Sign-On (SSO) is allowed. Default is selected.|  
|**Disable credential cache**|The SSO server stores credentials in a cache to expedite access. Default is not selected.|  
|**Tickets allowed**|Determines whether the SSO system uses tickets for this affiliate application. You must be an SSO administrator to select this option.|  
|**Validate tickets**|Determines whether the SSO system validates tickets when the user redeems them. You must be an SSO Administrator to select this option.|  
|**Timeout tickets**|Determines whether tickets have an expiration time. Default is checked. Unless it is required, do not disable ticket time-outs. You must be an SSO Administrator to set this option.|  
|**Ticket timeout (in minutes)**|Specifies a ticket time-out specific to the affiliate application. If ticketing is enabled for this application and this property is not, the time-out specified at the SSO System (Global) level is used. You must be an SSO Administrator to set this option.|  
|**Allow host initiated SSO**|Select this if Host initiated SSO is allowed. Default is not selected.|  
|**Verify external credentials**|Select to verify external credentials.|  
|**Direct Password Sync from Windows**|Select to allow Direct Password Sync for this application.|  
|**Application users cannot create mappings**|Increases system security by allowing only administrators to create mappings.|  
  
## See Also  
 [Enterprise Single Sign-On (Configuration)](../core/enterprise-single-sign-on-configuration-1.md)   
 [Create New Affiliate Application Wizard](../core/create-new-affiliate-application-wizard2.md)
