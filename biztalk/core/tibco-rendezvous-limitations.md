---
title: "TIBCO Rendezvous Limitations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TIBCO Rendezvous, limitations"
ms.assetid: 8e210457-2887-43f9-a249-be1daa6ee4eb
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# TIBCO Rendezvous Limitations
In TIBCO Rendezvous, field name uniqueness is not guaranteed. If a TIBCO Rendezvous message contains two field names that are the same, the resulting XML is not valid.  
  
 Other limitations include the following:  
  
-   Field ordering/sorting is not provided.  
  
-   According to TIBCO Rendezvous documentation, non-printable characters are not used in subject names; however, it is still possible that such characters are used. BizTalk Adapter for TIBCO Rendezvous does not support subject names containing those characters.  
  
-   Secure connection to daemons is not supported.  
  
-   Custom data types are not supported.  
  
-   Certified Messaging is not supported on the transmit side.  
  
## See Also  
 [TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md)   
 [Getting Started](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)