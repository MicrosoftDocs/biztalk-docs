---
description: "Learn more about: Before You Import the Management Pack"
title: "Before You Import the Management Pack"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Before You Import the Management Pack
As a best practice, you should import the Windows Server Management Pack for the operating system that you are using. Before you import the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack, take the following actions:  
  
-   Ensure that Operations Manager 2007 R2/2012 is installed.  
  
-   You must be a member of either the SCOM Administrators group or the SCOM Authors group. Local administrators on the SCOM Management Server have all the rights and permissions that are granted to the SCOM Administrators group.  
  
-   Set up your BizTalk Servers as managed computers in Operations Manager by deploying the SCOM agents on each BizTalk Server that you want to manage. The SCOM agent deployment involves the following tasks:  
  
    -   Install the SCOM agent.  
  
    -   Create a BizTalk SCOM agent account.  
  
    -   Configure a **Run As** account. Add the Run As account to the following groups:  
  
        -   BizTalk Groups.  
  
        -   BizTalk Administrators.  
  
        -   SSO Administrators.  
  
        -   SSO Affiliate Administrators.  
  
    -   Initiate monitoring.  
  
-   In Operation Manager Console, managed computers are in a healthy state.  
  
-   Configure any user accounts that have to be set up, such as any required Run As accounts or profiles. This management pack includes Run As profiles named “BizTalk Server Monitoring Account” and “BizTalk Server Discovery Account” to define specific credentials on a per-agent basis. You may have to use this Run As profile for some agents after you import the management pack.  
  
## In this section  
  
-   [Files in This Management Pack](../technical-guides/files-in-this-management-pack.md)  
  
-   [Recommended Additional Management Packs](../technical-guides/recommended-additional-management-packs.md)
