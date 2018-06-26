---
title: "Setting a Session Limit to Zero1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e47e4048-66be-4dfa-bedf-17c7e41dc6a4
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Setting a Session Limit to Zero
After **CNOS** raises the session limit above zero, it can reset the limit to zero only. It cannot set the session limit to a value that is not zero, and it cannot redistribute the number of sessions allocated as the contention winners and losers. Therefore, your program cannot change the mode session limits if the two logical units (LUs) have already set the limits to a nonzero value, regardless of which LU initiated the **CNOS** transaction.  

 A program can change the session limits from a nonzero value, as long as the program first changes the session limit to zero. For example, if the session limit is 8, a program can change it to 6 by first issuing **CNOS** and changing the session limit to zero, and then issuing **CNOS** again and setting the session limit to 6.  

 APPC can activate one or more LU-LU sessions with the specified mode name as a result of initializing the session limit. You cannot use **CNOS** to activate sessions between two LUs on the same server. APPC deactivates all LU-LU sessions for the specified mode name (or for all mode names for a partner LU) as a result of resetting the session limit to zero. APPC deactivates each session as it becomes free and does not interrupt active conversations.  

 A separate value, the maximum negotiable session limit, is used in **CNOS** negotiations. If the **set_negotiable** value is AP_YES, the mode session limit value given in this **CNOS** verb also sets the maximum negotiable session limit.  

 The **lu_alias** and **plu_alias** parameters are 8-byte ASCII character strings. If the name is fewer than eight bytes, it must be padded on the right with ASCII spaces.  

 You can specify the SNA-defined mode name SNASVCMG for **mode_name**. Use this mode only in a **CNOS** transaction when the source LU and the target LU use parallel user sessions. However, when resetting the session limits to zero for the SNASVCMG PU 2.1 node, the session limits of all other modes between the two LUs must be reset first. The PU 2.1 mode name is a type A EBCDIC character string. A mode name consisting of all spaces is supported. The SNA-defined mode name CPSVCMG is not allowed.  

 When specifying **plu_mode_sess_lim**, if the mode session limit is currently greater than zero, the value of this parameter must be zero. **CNOS** can raise the limit above zero, but the next **CNOS** must set the value to zero. A single **CNOS** cannot change the mode session limit from one nonzero number to another.  

 When raising the mode session limit above zero for a parallel-session connection, the target LU can negotiate its parameter to a value greater than zero and less than the specified session limit. The specified or negotiated limit then becomes the new mode session limit and is returned in this field.  

 The value specified for this parameter must be greater than or equal to the sum of the values specified in the **CNOS min_conwinners_source** and **min_conwinners_target** parameters.  

 Do not reset the SNASVCMG session limit to zero until all other mode session limits between the two LUs are reset to zero and the count of active sessions for all modes (except SNASVCMG) for the partner LU is zero.  

 The mode session limit should be large enough to accommodate all active conversations in the mode for all TPs.  

 For **min_conwinners_source** and **min_conwinners_target**, the sum of both parameters cannot exceed the mode session limit. For single-session connections, these parameters specify the desired contention-winner sessions for the target and source LUs. For the SNASVCMG mode name (with a mode session limit of 2 or 1), the specified minimum number of contention-winner sessions for the target LU must be 1. For the source LU, with a mode session limit of 2, the number must be 1; with a mode session limit of 1, the number must be 0. APPC uses these parameters only when the mode session limit is set to a nonzero value.  

 APPC uses auto_act only when the mode session limit is set to a nonzero value. If the value is greater than the min_conwinners_source value, APPC uses the new minimum number of contention winners for the source LU as the autoactivation limit.  

> [!CAUTION]
>  The **auto_act** parameter can conflict with the on-demand definition of a connection. Autoactivations by either peer partner can re-establish sessions and connections, possibly resulting in a thrashing situation. Therefore, avoid specifying autoactivation between peer PU 2.1 nodes using on-demand connections.  

 Whether an LU deactivates a session immediately after the current conversation or after all queued conversations are complete depends on the **drain_source** and **drain_target** parameters.  

 If an LU is to drain its waiting (outbound) allocation requests, it continues to allocate conversations to active sessions. The responsible LU deactivates a session only when the conversation allocated to the session is deallocated and no request is waiting for allocation to any session with the specified mode name between the two LUs. The allocation of a waiting request takes precedence over the deactivation of a session.  

 If an LU is not to drain its waiting (outbound) allocation requests, the responsible LU deactivates a session as soon as the conversation allocated to the session is deallocated. If no conversation is allocated to the session, the responsible LU deactivates the session immediately. However, this verb does not force deallocation of active conversations.  

 The **responsible** and **mode_name_select** parameters are interrelated as follows:  

- APPC ignores the **responsible** parameter for mode names for which the session limit is currently zero if this **CNOS** verb specifies **mode_name_select** (AP_ALL).  

- If CNOS specifies **mode_name_select** (AP_ONE) with a mode session limit of zero, and the current session limit for that mode name is already zero, the **responsible** parameter must specify the same LU (SOURCE or TARGET) that is currently responsible for deactivating sessions. APPC uses this parameter only when **CNOS** specifies a mode session limit of zero.  

  For parallel-session connections, the **drain_source** and **mode_name_select** parameters are interrelated as follows:  

- If **CNOS** specifies **mode_name_select** (AP_ALL) and **drain_source** (AP_YES), APPC ignores **drain_source** for those mode names for which the session limit is currently zero.  

- If **CNOS** specifies **mode_name_select** (AP_ALL) and **drain_source** (AP_NO), APPC accepts **drain_source** for all mode names. APPC ends draining for any mode currently draining its requests.  

- If **CNOS** specifies **mode_name_select** (AP_ONE), and **drain_source** (AP_YES) is currently in effect, **drain_source** (AP_NO) directs APPC to end the draining at the source LU for requests for the specified mode name.  

- If **CNOS** specifies **mode_name_select** (AP_ONE) and **drain_source** (AP_NO) is currently in effect, your program must specify **drain_source** (AP_NO) again.  

  For parallel-session connections, the **drain_target** parameter and the **mode_name_select** parameter are interrelated as follows:  

- If **CNOS** specifies **mode_name_select** (AP_ALL) and **drain_target** (AP_YES), APPC ignores **drain_target** for the mode names for which the session limit is currently zero.  

- If **CNOS** specifies **mode_name_select** (AP_ALL) and **drain_target** (AP_NO), APPC accepts **drain_target** for all mode names, regardless of the current session limit. Any draining of waiting (outbound) allocation requests at the target LU is ended.  

- If **CNOS** specifies **mode_name_select** (AP_ONE) and **drain_target** (AP_YES) is currently in effect, **drain_target** (AP_NO) ends the target LUs draining.  

- If **CNOS** specifies **mode_name_select** (AP_ONE) and **drain_target** (AP_YES), and **drain_target** (AP_NO) is currently in effect, the target LU can either accept **drain_target** (AP_YES) or negotiate the parameter to AP_NO. After the target LU accepts the **drain_target** (AP_YES) parameter, it can drain any remaining waiting (outbound) allocation requests.
