---
title: "The Auto-Enlist and Approval Process | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dfd3e72e-e28b-4ee3-bc4a-89ef3f64e6d5
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The Auto-Enlist and Approval Process
You can configure the ESB Management Portal to publish Microsoft BizTalk Server endpoints in two ways:  
  
- It can be configured through the approval process, where an administrator must confirm and approve the registration request.  
  
- It can be configured by using auto-publish, where the portal automatically publishes the request into the Universal Description, Discovery, and Integration (UDDI) registry without requiring administrator intervention.  
  
  You can also specify several other settings of the UDDI Integration features of the portal, as described in the following two procedures.  
  
### To configure auto-approval and publishing in the ESB Management Portal  
  
1.  Make sure that you log on to the portal using an account that is a member of the BizTalk Server Administrators group.  
  
2.  Point to the **Admin** tab on the portal main menu, and then click **Registry Settings** to open the portal [Registry Settings Page](../esb-toolkit/registry-settings-page.md).  
  
3.  To enable auto-approval and publishing, type the URL of your UDDI server in the text box at the top of the **UDDI Details** section of the page, and then select the **AutoPublish** check box.  
  
4.  To disable auto-approval and publishing, clear the **Auto Publish** check box.  
  
### To configure e-mail and registry settings for the UDDI Integration features  
  
1.  Make sure that you log on to the portal using an account that is a member of the BizTalk Server Administrators account group.  
  
2.  Point to the **Admin** tab on the portal main menu, and then click **Registry Settings** to open the portal [Registry Settings Page](../esb-toolkit/registry-settings-page.md).  
  
3.  Edit the URL of your UDDI server in the text box at the top of the **UDDI Details** section of the page. The default UDDI service is the local Microsoft UDDI service.  
  
4.  Select the **Anonymous** check box if you want the portal to use anonymous authentication when accessing the UDDI server.  
  
5.  If you want the portal to notify you by e-mail when a UDDI publishing request is awaiting approval, select the **Notification Enabled** check box in the **Email Notification** section of the page. Then enter the details of your e-mail server, the address for delivery of e-mail messages, an appropriate "from" e-mail address, the message subject, and the message body.  
  
6.  Enter the administrator contact name and e-mail address for the receipt of UDDI request e-mail messages in the **Default Settings** section of the page.  
  
### To approve or decline a registration request as an administrator  
  
1.  Make sure that you log into the portal using an account that is a member of the BizTalk Server Administrators group.  
  
2.  Point to the **Registry** tab on the portal main menu, and then click **Manage Pending Requests** to open the portal [Manage Pending Requests Page](../esb-toolkit/manage-pending-requests-page.md).  
  
3.  To approve a pending request, click the **Approve** icon (the check mark) next to that request in the list.  
  
4.  To reject a pending request, click the **Reject** icon (the cross mark) next to that request in the list.  
  
5.  To view details of a pending request, click the **View Details** icon (the magnifying glass) to open the [Registry Details Page](../esb-toolkit/registry-details-page.md). You can publish, delete, or update the request in this page.  
  
6.  To review the requests status and see a list of previous requests, click the **View Request History** link.