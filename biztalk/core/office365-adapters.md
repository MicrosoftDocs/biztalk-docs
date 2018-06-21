---
title: "Use the Office 365 Outlook Email adapter | Microsoft Docs"
description: Send and receive messages using the Office 365 Outlook adapters in BizTalk Server
ms.custom: ""
ms.date: "06/19/2018"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
author: "MandiOhlinger"
ms.author: "ribarua"
manager: "sangupt"
---

# Office 365 Outlook adapters in BizTalk

## Overview
**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 3**, you can send and receive messages between BizTalk Server and Office365 Outlook features.
The following adapters have been added as part of Feature Pack 3.

1. [Office365 Outlook Email adapter](./office365-mail-adapter.md)
2. [Office365 Outlook Calendar adapter](./office365-calendar-adapter.md)
3. [Office365 Outlook Contact adapter](./office365-contact-adapter.md)

## Prerequisites

* Have an [Office365 account](https://outlook.office365.com)
* Install [Feature Pack 3](https://aka.ms/bts2016fp3) on your BizTalk Server
* Install BizTalk Server TMS Service.

## BizTalk Server TMS

BizTalk Server TMS is a service which refreshes the Office365 OAuth tokens used by BizTalk periodically, ensuring that the tokens always remain valid. 
It has a dependency on Enterprise Single Sign On service and must be installed on a machine which hosts the master secret server. 

## Installing BizTalk Server TMS

1. Run BizTalkTMS.msi from **< BizTalk Installation Folder\BizTalkTMS.msi >** after installing Feature Pack 3
1. Fill in the username and password to install the BizTalk Server TMS service.
2. The user for the installer must be a member of the SSO Administrators group. 

![BizTalk Server TMS setup](../core/media/BizTalk-TMS.png)

## Sign-in for Office 365 Adapters in BizTalk

1. Create a Send/Receive location and click configure.
2. Click the **Sign-in...** in the Send/Receive Location configuration in BizTalk Administration console.
3. Select the Office 365 account to sign into.

![Office 365 Sign in](../core/media/office365-signin.png)

4. Enter credentials and confirm permissions. These credentials are used to authorize BizTalk to connect to and access the Office 365 account.

The following shows permissions for Office 365 Outlook Calendar:

![Office 365 Calendar permissions](../core/media/office365-calendar-permissions.png)