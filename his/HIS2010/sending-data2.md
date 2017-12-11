---
title: "Sending Data2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55a7427e-661c-4cb7-9fd9-cfecf01fa9e5
caps.latest.revision: 3
---
# Sending Data
The following calls are used to send data to the partner program:  
  
> [!NOTE]
>  The names of the calls are pseudonyms. The actual C function names appear in parentheses after the pseudonyms. For example, **Accept_Conversation** is the pseudonym for a call. The actual function name is **cmaccp**.  
  
 [Confirm](../HIS2010/confirm-cpi-c-1.md)( **cmcfm**)  
 Sends the contents of the local logical unit's (LU) send buffer and a confirmation request to the partner program and waits for confirmation.  
  
 [Flush](../HIS2010/flush-cpi-c-1.md)( **cmflus**)  
 Sends the contents of the local LU's send buffer to the partner LU (and partner program). If the send buffer is empty, no action takes place.  
  
 [Prepare_To_Receive](../HIS2010/prepare-to-receive-cpi-c-2.md)( **cmptr**)  
 Changes the state of the conversation for the local program from SEND to RECEIVE, making it possible for the local program to begin receiving data. Before changing the conversation state, this call performs the equivalent of the **Flush** or **Confirm** call.  
  
 [Request_To_Send](../HIS2010/request-to-send-cpi-c-2.md)( **cmrts**)  
 Notifies the partner program that the local program wants to send data. The partner program may or may not act on this request.  
  
 [Send_Data](../HIS2010/send-data-cpi-c-1.md)( **cmsend**)  
 Puts data in the local LU's send buffer for transmission to the partner program. The data collected in the local LU's send buffer is transmitted to the partner LU (and partner program) when one of the following occurs:  
  
-   The send buffer fills up.  
  
-   The local program issues a **Flush**, **Confirm**, or [Deallocate](../HIS2010/deallocate-cpi-c-2.md) call or other call that flushes the LU's send buffer. (Some send types, set by **Set_Send_Type**, include flush functionality.)  
  
 [Set_Prepare_To_Receive_Type](../HIS2010/set-prepare-to-receive-type-cpi-c-2.md)( **cmsptr**)  
 Sets the conversation's prepare-to-receive type, which specifies whether subsequent **Prepare_To_Receive** calls will include **Flush** or **Confirm** functionality. The prepare-to-receive type affects all subsequent **Prepare_To_Receive** calls. It can be changed by reissuing **Set_Prepare_To_Receive_Type**.  
  
 [Set_Send_Type](../HIS2010/set-send-type-cpi-c-1.md)( **cmsst**)  
 Sets the conversation's send type. The send type specifies how data will be sent by **Send_Data**. The send type can specify that only data be sent or that, in addition to sending data, Common Programming Interface for Communications (CPI-C) executes the equivalent of **Flush**, **Confirm**, **Prepare_To_Receive**, or [Deallocate](../HIS2010/deallocate-cpi-c-2.md). The send type value affects all subsequent **Send_Data** calls. It can be changed by reissuing **Set_Send_Type**.