---
description: "Learn more about: Single Sign-On: Event 10843"
title: "Single Sign-On: Event 10843"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10843
## Details  
  
| Field | Error Details |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                      Enterprise Single Sign-On                                                                      |
| Product Version |                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                      |
|    Event ID     |                                                                                10843                                                                                |
|  Event Source   |                                                                               ENTSSO                                                                                |
|    Component    |                                                                                 N/A                                                                                 |
|  Symbolic Name  |                                                                         ENTSSO_E_NO_SECRET2                                                                         |
|  Message Text   | Cannot perform encryption or decryption because the secret is not available from the master secret server. See the event log (on computer ‘%1’) for related errors. |
  
## Explanation  
 Access is denied.  
  
## User Action  
 Either the master secret server is off-line, or the master secret server is missing the required master secret. See the event log on the specified computer for related errors.
