---
title: "SSO with Encrypted Passwords2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5136454e-64f9-412d-a6b3-b43677292108
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# SSO with Encrypted Passwords
If you are using Single Sign-On (SSO) security, you must determine whether the client application passes plain text passwords or encrypted passwords to the Transaction Integrator (TI) run-time environment. If the passwords are in plain text, SSO accepts the passwords when they are submitted by the TI run-time environment. If the passwords are encrypted, SSO does not accept the passwords, and the call to SSO fails. To avoid failed SSO calls, disable password validation for the SSO affiliate application.