---
title: "SNA Host Environments | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2914ce6e-c2f6-4e65-80fc-5f0acb64dd1d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SNA Host Environments
Host Environment(s) must be defined for each host endpoint that will make a call to a HIP Service. When using APPC, the HIP Service identifies the incoming call via the incoming Logical Unit (LU) name.  If an incoming call is received from an unknown LU, the TI runtime will not respond to the request and will log an event in the application event log to indicate an unknown host resource attempted to make a call.

- In the right-hand pane, the following information is required:
    - **Code Page**.  The default code page is 37.
    - **Data Conversion**.  Select between OS390 (mainframe) or AS400 (mid range iSeries).
    - **Name**.  The name to use for this SNA Host Environment.
    - **Timeout**.  The timeout value in seconds that will be used by the TI Runtime when communicating with the host.
    - **Remote LU Name**.  The LU name for the incoming LU.  This LU will be configured in the SNA Manager as a Remote LU.
    