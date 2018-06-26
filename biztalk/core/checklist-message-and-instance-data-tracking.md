---
title: "Checklist: Message and Instance Data Tracking | Microsoft Docs"
description: Best practices when tracking messages, instances, and artifacts in BizTalk Server
ms.custom: ""
ms.date: "02/26/2018"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4b5b614-23e5-4895-9c66-417b55dee43c
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Message and Instance Data Tracking

|Step|Reference|  
|----------|---------------|  
|Review the message and service instance data tracking  security considerations|[Security Considerations for Message and Instance Data Tracking](../core/security-considerations-for-message-and-instance-data-tracking.md)|  
|Review the  message and service instance data tracking best practices|[Best Practices for Message and Instance Data Tracking](../core/best-practices-for-message-and-instance-data-tracking.md)|  
|Ensure that the SQL Server Agent service is running on all MessageBox databases|SQL Server Agent makes message bodies available message tracking and WMI, and enables you to run jobs to clean up the MessageBox databases.<br /><br /> See SQL Server Books Online for more information about SQL Server Agent and the SQL Server Agent service.|  
|Configure tracking on artifacts in the BizTalk Server Administration Console|[Orchestration tracking](how-to-configure-tracking-for-an-orchestration.md)<br/>[Send port tracking](how-to-configure-tracking-for-a-send-port.md)<br/>[Receive port tracking](how-to-configure-tracking-for-a-receive-port.md)<br/>[Policy tracking](how-to-configure-tracking-for-a-policy.md)<br/>[Schema tracking](how-to-configure-tracking-for-a-schema.md)<br/>[Pipeline tracking](how-to-configure-tracking-for-a-pipeline.md)|  

## See Also  
 [Best Practices for Message and Instance Data Tracking](../core/best-practices-for-message-and-instance-data-tracking.md)
