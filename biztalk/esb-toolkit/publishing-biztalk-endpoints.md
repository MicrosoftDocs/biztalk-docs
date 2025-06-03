---
description: "Learn more about: Publishing BizTalk Endpoints"
title: "Publishing BizTalk Endpoints"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Publishing BizTalk Endpoints
You can use the ESB Management Portal to create and publish entries into the currently configured Universal Description, Discovery, and Integration (UDDI) server.  
  
### To publish a Microsoft BizTalk Server endpoint into the current UDDI server  
  
1.  Point to the **Registry** tab on the portal main menu, and then click **New Registry Entry** to open the [New Registry Entry Page](../esb-toolkit/new-registry-entry-page.md).  
  
2.  Use the drop-down lists on the page to filter on the endpoint type, the status, and the application where the endpoint resides.  
  
3.  Click the arrow icon next to the endpoint you want to publish to create a UDDI registration request.  
  
4.  If an administrator has enabled auto-publishing of endpoints, the portal automatically publishes the new entry into the UDDI server.  
  
5.  If an administrator has not enabled auto-publishing of endpoints, the requests remains in the queue until an administrator approves or declines the request.
