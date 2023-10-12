---
description: "Learn more about: ESSO Security Policies"
title: "ESSO Security Policies"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ESSO Security Policies
Enterprise Single Sign-On (ESSO) Security policies define how Windows security credentials are established before the HIP server object is run. The security credentials can be based on the user IDs and passwords delivered to HIP by either the client application program or ESSO. If there is no ESSO Security Policy defined, then the security credentials of the user the HIP Service is running as are used.

 [!NOTE] In the right-hand pane the following information can be entered:
 - **Name**. The name for the Security Policy.
 - **Default Credentials Group**.  The credential group is used to create a default Windows login environment when a host user name is not available from the protocol data stream.
 - **Affiliate Application**. The defined Affiliate Application within ESSO.  This must be either a Host Group or Individual affiliate application.
