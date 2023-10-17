---
description: "Learn more about: MQ Channel (MQ Channel Library Wizard)"
title: "MQ Channel (MQ Channel Library Wizard)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "mqb_mqi_channels_tab"
ms.assetid: 53c055da-8059-4373-9aa3-cb6931c13ab8
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# MQ Channel (MQ Channel Library Wizard)
Specify information for the MQ channel to connect to the host.  
  
|Use this|To do this|  
|--------------|----------------|  
|Connection Name|Type the name of the server that the remote MQ manager is running on.|  
|Connection Type|Select one of the following connection types.<br /><br /> -   **Base Client**<br /><br /> -   **ExtendedClient**<br /><br /> -   **Server**|  
|Transport Type|Select one of the following supported transport types.<br /><br /> -   **TCP**<br /><br /> -   **LU6.2**|  
|Channel Name|Type the case-sensitive name of the server connection channel.|  
|Request URI|Type the request URI using the specified format. The system name must be part of the URI.<br /><br /> \<*Connection Name*>/\<*Queue Manager Name*>/\<*Queue Name*>|  
|Response URI|Retrieves the message from the host. The response URI using the same string value as the request URI.<br /><br /> \<*Connection Name*>/\<*Queue Manager Name*>/\<*Queue Name*>|  
  
## See Also  
 [MQ Channel Library Wizard](../core/mq-channel-library-wizard1.md)
