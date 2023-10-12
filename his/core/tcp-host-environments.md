---
description: "Learn more about: TCP Host Environments"
title: "TCP Host Environments"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# TCP Host Environments
TCP Host Environment(s) must be defined for each host endpoint that will make a call to a HIP Service via TCP/IP. The HIP Service identifies the incoming call via the incoming IP address.  If an incoming call is received from an unknown address, the TI runtime will not respond to the request and will log an event in the application event log to indicate an unknown host attempted to make a call.

- In the right-hand pane, the following information is required:
    - **Code Page**.  The default code page is 37.
    - **Data Conversion**.  Select between OS390 (mainframe) or AS400 (mid range Power Series).
    - **Name**.  The name to use for this TCP Host Environment.
    - **Timeout**.  The timeout value in seconds that will be used by the TI Runtime when communicating with the host.
    - **IP Address**.  The IP Address or dns name of the backend system.
