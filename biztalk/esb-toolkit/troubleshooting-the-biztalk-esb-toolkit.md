---
title: "Troubleshooting the BizTalk ESB Toolkit"
description: Troubleshoot installation issues, and common errors with the ESB Toolkit in BizTalk Server
ms.custom: ""
ms.date: "08/10/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: troubleshooting-general
---

# Troubleshoot the BizTalk ESB Toolkit


## Installation

- You receive an "Error assigning permissions" exception during installation.

  **Resolution**: The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] uses the standard BizTalk account groups, which must exist during the installation process or the installation will fail. In addition, the toolkit assumes either a standalone installation where the computer is a member of a workgroup or an enterprise installation where the computer is a member of a domain.

- Application import fails with an error message that warns of trust level mismatch.

   **Resolution**: The Microsoft.BizTalk.ESB binding files are configured to work with the default BizTalkServerApplication and BizTalkServerIsolatedHost, which are in turn configured to execute in untrusted mode. If you have changed your host to run in trusted mode, the binding file will not import. To correct this, you must either change the trust level to untrusted or edit the binding file to suit your environment in the BizTalk Toolkit \Bindings directory.

- Kerberos authentication is not configured in Internet Information Services (IIS).

   **Resolution**: Enable Kerberos authentication for IIS. [Kerberos Constrained Delegation Overview](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) may be a good resource.

## General Issues

- You receive an "Internal SOAP Processing" exception when sending a message to the generic ESB Itinerary On-Ramp Web service.

  **Resolution**: Use the BizTalk Server Administration Console to ensure that the Microsoft.Practices.ESB application is running; if it is not running, start it.

- Exception messages are not appearing in the ESB Management Portal site.

  **Resolution**: Check the BizTalk Administrator Group Overview page and the Windows Application Event Log for entries that indicate failures to send messages. You may need to reconfigure the exception Send Adapter (part of the Microsoft.Practices.ESB application) to match your environment. In addition, be aware that both the BizTalk Failed Message Routing feature and the BizTalk ESB Toolkit Exception Management Framework generate exceptions messages. Therefore, ensure that you enable the **Route on Failed Messages** option for send and receive ports.

- When consuming a WCF service with a static resolver, you receive an invalid SOAP action exception.

  **Resolution**: If the WCF service SOAP action does not include the target namespace, set the value of the SOAP action in the following format in the resolver setting: {action} to indicate that the target namespace will not be concatenated by the ESB Toolkit core engine at runtime.
