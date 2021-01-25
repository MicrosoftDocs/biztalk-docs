---
description: "Learn more about: Invoking TPs and Contention (CPI-C)"
title: "Invoking TPs and Contention (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6564c8a-1930-4c42-aa94-46286f9e395d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Invoking TPs and Contention (CPI-C)
The following information applies only to cases where logical units (LUs) are communicating in complex ways (such as chains of LUs) over multiple sessions. In such cases, two LUs may attempt to allocate a conversation on the same session at the same time. If this happens, one LU must win (the contention winner) and one must lose (the contention loser). The contention-winner LU and the contention-loser LU are determined for each session when the session is established. During that particular session, the contention-loser LU must receive permission from the contention-winner LU before allocating a conversation. In contrast, the contention-winner LU on that session allocates a conversation as needed.  
  
 Note that when two LUs are communicating over multiple sessions, one LU can be the contention winner for some of the sessions, and the other LU the contention winner for others.  
  
 An invoking transaction program (TP) operates most efficiently if the number of concurrent [Allocate](./allocate-cpi-c-2.md) requests that the TP issues is matched by the number of sessions on which the local LU is the contention winner. The choice of contention winner is controlled through the modes configured at the two ends of the communication. A mode must be configured to work with the mode on the remote system for communication to begin between two LUs.
