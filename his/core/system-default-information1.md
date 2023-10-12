---
description: "Learn more about: System Default Information"
title: "System Default Information1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# System Default Information

System default information is defined or returned as described here.  
  
## Defined by IBM ES for OS/2 version 1.0  
  
The system default information defined by IBM ES for OS/2 version 1.0 contains the following members:
  
*default_mode_name*  
Mode name used for undefined mode name is sent or received.  
  
*default_local_lu_name*  
Alias or local default LU.  
  
*implicit_partner_lu_support* 
Indicates if implicit partner LU support is enabled.  
  
*maximum_held_alerts*  
Number of alerts that will be held by NS/2 if there is no active link to a focal point.  
  
*default_tp_conversation_security_rqd* 
Specifies if conversation security is used for default TPs.  
  
*maximum_mc_ll_send_size*  
Maximum length of a logical record used on a mapped conversation for sending data to either the inbound or outbound implicit remote LU.  
  
*directory_for_inbound_attaches*  
Name of OS/2 directory used by Attach Manager.  
  
*default_tp_operation*  
Set to one of the following:  
  
- QUEUED_OPERATOR_STARTED  
- QUEUED_OPERATOR_PRELOADED  
- QUEUED_AM_STARTED  
- NONQUEUED_AM_STARTED  

*default_tp_program_type*  
Set to one of the following:  
  
- BACKGROUND  
- FULL_SCREEN  
- PRESENTATION_MANAGER  
- VIO_WINDOWABLE  
  
## Returned by Host Integration Server  
  
The system default information returned by Host Integration Server contains the following members:
  
*default_mode_name*  
Always set to NULL.  
  
*default_local_lu_name*  
Always set to spaces.  
  
*implicit_partner_lu_support*  
Always set to NO.  
  
*maximum_held_alerts*  
Always set to zero.  
  
*default_tp_conversation_security_rqd*  
Always set to NO.  
  
*maximum_mc_ll_send_size*  
Always set to 16384.  
  
*directory_for_inbound_attaches*  
Always returned * and indicates that the current path should be used.  
  
*default_tp_operation*  
Always set to QUEUED_AM_STARTED.  
  
*default_tp_program_type*  
Always set to FULL_SCREEN.