---
description: "Learn more about: Global Settings Tab"
title: "Global Settings Tab"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: how-to
f1_keywords: 
  - "btahl7.configurationexplorer.tab.globalsettings"
---
# Global Settings Tab
You use the **Global Settings** tab to configure the logging store used by [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].  

 In the **BTAHL7 Configuration Explorer** dialog box, on the **Global Settings** tab, do the following:  


|     Use this      |                                                                                                                                                To do this                                                                                                                                                |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **WMI**      |                                                                 Select this option if you want to generate [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Management Instrumentation (WMI) notifications for BTAHL7.                                                                  |
|      **SQL**      | Select this option if you want to use Microsoft [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] as your logging store for BTAHL7. **Note:**  BTAHL7 automatically creates the tables required for logging if they do not exist. |
|  **SQL Server**   |            Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] name. This is required when you select the **SQL** option. The maximum allowed length is 64 characters.<br /><br /> The default server and database name is the configured BTAHL7 database.            |
| **Database name** |                                                 Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database name. This is required when you select the **SQL** option. The maximum allowed length is 128 characters.                                                 |
|   **Event Log**   |                Select this option if you want to use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Log as the logging store for BTAHL7. You use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Viewer to view event messages.                 |

