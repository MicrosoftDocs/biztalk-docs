---
description: "Learn more about: Common Problems"
title: "Common Problems2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40adc313-75db-48c6-b61c-61688f4cae4f
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Common Problems
The Host Print Service runs under a Windows user context. The Host Print Service (SnaPrint) may not be running under a Windows user context that has authority to open a session to the destination printer. Confirm the user context of the Host Print Service, and/or try re-entering the password within the Services Control Panel for SnaPrint Startup, within "Log On As: This Account:". In addition, the user's rights can be confirmed by logging on to [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] as that user and attempting to print from Notepad.

 The Generic/Text only printer driver has several limitations. Please see the following Microsoft Knowledge Base articles (available from the Web site [http://go.microsoft.com/fwlink/?LinkID=99570](https://go.microsoft.com/fwlink/?LinkID=99570)):

 168233: [http://support.microsoft.com/kb/168233](https://support.microsoft.com/kb/168233)

 166000: [http://support.microsoft.com/kb/166000](https://support.microsoft.com/kb/166000)

 162616: [http://support.microsoft.com/kb/162616](https://support.microsoft.com/kb/162616)

 154322: [http://support.microsoft.com/kb/154322](https://support.microsoft.com/kb/154322)

 Transparent sections in print jobs will be discarded unless a PDT file is configured. When such sections are discarded, an Even is logged in the Event Log, with a sample of the discarded data. This logging can be disabled globally from the Properties Page of the Print Server in SNA Manager.

 HP PCL escape sequences in transparent sections should use all ASCII characters.

 In addition the session property **Transparent is ASCII** must be selected.

 If printing through cascaded Windows print servers, it may be necessary to add the printer share name to the NullSessionShares Registry entry on the Windows computer to which the Host Print Service is printing:

```
HKEY_LOCAL_MACHINE
   System/CurrentControlSet
     Services
       LanmanServer
          Parameters
             NullSessionShares:  REG_MULTI_SZ:  <sharename>

```

 Where \<sharename> is the share name associated with the Windows printer. Note that each share name must be listed on a separate line within the Regedit.exe "Multi-String editor". The Windows computer must be rebooted to enable this change. See Microsoft Knowledge Base article 121853 at: [http://support.microsoft.com/kb/121853](https://support.microsoft.com/kb/121853).
