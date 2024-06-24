---
description: "Learn more about: What Version of BizTalk Server Do I Have?"
title: "What Version of BizTalk Server Do I Have?"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# What Version of BizTalk Server Do I Have?
You may be running different versions and different editions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This topic shows you how to determine [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation information, including the version number, edition, and installation path.

## Use the registry

1. Select **Start**, type `regedt32`, and then open it.

2. Expand **HKEY_LOCAL_MACHINE**, expand **SOFTWARE**, expand **Microsoft**, expand **BizTalk Server**, and then select **3.0**.

3. The right pane displays installation information, including:


   |      Sub-key       |                                                                                                         Description                                                                                                          |
   |--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |  **InstallPath**   |                                             Lists the installation path where you installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].                                              |
   | **ProductEdition** |                                                        Lists the edition, including:<br /><br /> -   Developer<br />-   Branch<br />-   Standard<br />-   Enterprise                                                         |
   | **ProductVersion** | Lists the base product version. For specific product version, including service packs and cumulative updates, see [BizTalk Versions](/archive/technet-wiki/7915.biztalk-server-versions). |

## Use the control panel

1.  Select **Start**, type `Programs and Features`, and then open it.

2. In the list, select **Microsoft BizTalk Server**. The version and edition are listed.

See [BizTalk Versions](/archive/technet-wiki/7915.biztalk-server-versions).

## See Also
 [Get started](../core/getting-started-with-biztalk-server.md)
