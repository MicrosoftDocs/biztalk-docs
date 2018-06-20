---
title: "APPC Management Verbs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8f2d680-7888-4762-b043-4a5131933017
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# APPC Management Verbs
This section describes the Advanced Program-to-Program Communications (APPC) management verbs. The management verbs enable you to establish APPC LU 6.2 session limits, obtain configuration information and current operating values for the SNA node, and activate or deactivate sessions. The description of each verb provides:  
  
- A definition of the verb.  
  
- The structure defining the verb control block (VCB) used by the verb. The structure is contained in the WINAPPC.H file. The length of each VCB field is in bytes. Fields beginning with reserv (for example, reserv2) are reserved.  
  
- The parameters (VCB fields) supplied to and returned by APPC. A description of each parameter is provided, along with its possible values and other information.  
  
- The conversation state(s) in which the verb can be issued.  
  
- The state(s) to which the conversation can change upon return from the verb. Conditions that do not cause a state change are not noted. For example, parameter checks and state checks do not cause a state change.  
  
- Additional information describing the verb.  
  
  Most parameters supplied to and returned by APPC are hexadecimal values. To simplify coding, these values are represented by meaningful symbolic constants, which are established by **#define** statements in the WINAPPC.H header file. For example, the **opcode** (operation code) member of the **mc_send_data** structure used by the **MC_SEND_DATA** verb is the hexadecimal value represented by the symbolic constant AP_M_SEND_DATA. Use only the symbolic constants when writing transaction programs (TPs).  
  
## In This Section  
  
-   [ACTIVATE_SESSION](../core/activate-session2.md)  
  
-   [CNOS](../core/cnos2.md)  
  
-   [DEACTIVATE_SESSION](../core/deactivate-session1.md)  
  
-   [DISPLAY](../core/display2.md)