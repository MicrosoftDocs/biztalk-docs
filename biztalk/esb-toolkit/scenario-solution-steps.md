---
description: "Learn more about: Scenario Solution Steps"
title: "Scenario Solution Steps"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Scenario Solution Steps
The ESB Exception Management Framework provides a simple solution for handling an exception when an invoice message contains invalid data that causes an error during processing, as described earlier in this topic. The following is one approach you could take:  
  
1.  Assign responsibility for the recently deployed Financial Reporting application based on Microsoft BizTalk to a developer on your team.  
  
2.  A new ESB fault message arrives in the ESB Management Portal; the message indicates a data integrity issue in an orchestration in the Financial Reporting BizTalk application.  
  
3.  The administrator or operator notifies the developer of the new exception, or the developer registers for automatic notification when an exception occurs. This notification may occur for one of the following reasons:  
  
    -   It may occur because the exception exceeded a threshold predefined in event-based Business Activity Monitoring (BAM).  
  
    -   It may occur because a BizTalk subscription exists for the specific application, service, scope, and fault code that forwards the exception to the developer.  
  
4.  The developer examines the fault message, the individual orchestration messages, and their persisted context property values. Developers can view this information through the ESB Management Portal or by using Microsoft Outlook through a BizTalk subscription.  
  
5.  The developer determines that this is a common error. It will require manual intervention and correction by the Finance team, followed by resubmission to the system.  
  
6.  The developer creates and deploys an independent BizTalk orchestration project that subscribes to the specific application and exception type.  
  
7.  The orchestration project retrieves the invalid message from the ESB fault message, sends the message to the Finance team for correction, correlates the corrected message back to the orchestration, and resubmits it.  
  
8.  A week later, the developer navigates to the ESB Management Portal to discover that application exception trends for invalid messages have decreased dramatically since this solution was deployed.
