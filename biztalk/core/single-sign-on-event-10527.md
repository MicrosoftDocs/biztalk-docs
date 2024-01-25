---
description: "Learn more about: Single Sign-On: Event 10527"
title: "Single Sign-On: Event 10527"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10527
## Details  

| Field | Error Details |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                      Enterprise Single Sign-On                                                                                      |
| Product Version |                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                      |
|    Event ID     |                                                                                                10527                                                                                                |
|  Event Source   |                                                                                               ENTSSO                                                                                                |
|    Component    |                                                                                                  0                                                                                                  |
|  Symbolic Name  |                                                                                     SSO_ERROR_GET_SECRET_FAILED                                                                                     |
|  Message Text   | A request to get a master secret failed.%r<br /><br /> Secret Number: %1%r<br /><br /> Client User: %2%r<br /><br /> Client Computer: %3%r<br /><br /> Tracking ID: %4%r<br /><br /> Error Code: %5 |

## Explanation  
 This Error event indicates that a request to get the master secret has failed. In these cases there should be related messages in the Application event log.  

## User Action  
 To resolve this error, do the following:  

- Check the Application event log for associated events or errors.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md)  

- [Managing the Master Secret](../core/managing-the-master-secret.md)
