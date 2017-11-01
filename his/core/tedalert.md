---
title: "Tedalert2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f2c2aaf-8ae7-4343-9351-0374bd997d4a
caps.latest.revision: 3
---
# Tedalert
The alert information record tedalert includes details of a 3270 NetView user alert.  
  
## Syntax  
  
```  
  
typedef struct tedalert {  
    UCHAR    dalrtnam[53];  
    UCHAR    daparam1[33];  
    UCHAR    daparam2[33];  
    UCHAR    daparam3[33];  
} TEDALERT;  
```  
  
## Remarks  
 The following "Members" list explains the meaning of each field in the structures that is relevant to the application and indicates how the application should use each field. Fields that are not included in the list are used by other Microsoft® Host Integration Server components and need not concern the application; in particular, the network management connection name and the times at which RTM data is sent to the host are handled by the local node on behalf of the application.  
  
 Note that the application should determine whether the user is permitted to send NetView user alerts and/or view RTM data (see [3270 User Record Format](../core/3270-user-record-format.md)). It should not display the appropriate information, as described below, if the user does not have permission to use that information. The host can also override whether the application is permitted to send and/or to display RTM data (for more information, see [RTM Parameters](../core/rtm-parameters].md)).  
  
 For more information about how the application uses the RTM parameters, see [RTM Parameters](../core/rtm-parameters].md), [Response Time Monitor Data](../core/response-time-monitor-data.md), and [Status-RTM](../Topic/Status-RTM2.md).  
  
## Members  
 *dalrtnam[53]*  
 The description (up to 52 characters) of the alert corresponding to a particular alert number. The application should display this information to help the user determine which alert to send.  
  
 *daparam1[33]*  
 The descriptions (each up to 32 characters) of up to three parameters.  
  
 *daparam2[33]*  
 Required for the alert; depending on the specific alert.  
  
 *daparam3[33]*  
 One or more of these descriptions can be blank, indicating that the parameter is not used. For each of these descriptions that is not blank, the application should display this string to prompt the user for the appropriate parameter.