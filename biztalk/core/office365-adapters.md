---
title: "Use the Office 365 Outlook Email adapter | Microsoft Docs"
description: Overview of sending and receiving messages using the Office 365 Outlook adapters in BizTalk Server, including Email, Calendar, and Contacts
ms.custom: ""
ms.date: "03/05/2020"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
author: "MandiOhlinger"
ms.author: "ribarua"
manager: dougeby
---

# Office 365 Outlook adapters in BizTalk

## Overview

Use the Office 365 Outlook adapters in BizTalk to send and receive messages between BizTalk Server and Office 365 Outlook features:

- [Office 365 Outlook Email adapter](../core/office365-mail-adapter.md)
- [Office 365 Outlook Calendar adapter](../core/office365-calendar-adapter.md)
- [Office 365 Outlook Contact adapter](../core/office365-contact-adapter.md)

## Prerequisites

- Have an [Office 365 account](https://outlook.office365.com)
- [Configure BizTalk TMS service](../core/configure-biztalk-server.md#configure-biztalk-tms)

## TMS overview

BizTalk TMS is a service that manages the Office 365 OAuth tokens used by BizTalk. It refreshes these tokens periodically, ensuring that the tokens always remain valid.

## Sign-in to Office 365

When you're creating a [send port](../core/how-to-create-a-send-port2.md) or [receive location](../core/how-to-create-a-receive-location.md) in BizTalk Administration and choose any of the Office 365 adapters, you need to **Sign-in...** to your Office 365 account:

> [!div class="mx-imgBorder"]
> ![Office 365 Sign in](../core/media/office365-signin.png)

You enter the Office 365 credentials, and confirm permissions. These credentials authorize BizTalk to connect to, and access the Office 365 account. In the following example, you see the permissions for Office 365 Outlook Calendar:

> [!div class="mx-imgBorder"]
> ![Office 365 Calendar permissions](../core/media/office365-calendar-permissions.png)

## Next steps

- [Office 365 Outlook Email adapter](./office365-mail-adapter.md)
- [Office 365 Outlook Calendar adapter](./office365-calendar-adapter.md)
- [Office 365 Outlook Contact adapter](./office365-contact-adapter.md)
