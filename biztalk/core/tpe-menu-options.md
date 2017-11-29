---
title: "TPE Menu Options | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tracking Profile Editor, menu options"
  - "activities [BAM], importing"
  - "activities [BAM], definitions"
ms.assetid: 5179fcb5-6dab-481d-ad89-3868c8b07383
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# TPE Menu Options
This topic describes the menu options of the Tracking Profile Editor (TPE). The main menus include File, Tools, and Help.  
  
 Additional functionality specific to messaging interception is exposed on the context menu of items displayed in the Activity View in the left pane of the application.  
  
## File Menu  
 The File menu contains the following options:  
  
-   **New** – Creates a new tracking profile. This option is always available.  
  
-   **Open** – Opens an existing tracking profile. This option is always available.  
  
-   **Save** – Saves the tracking profile currently being edited. If no tracking profile is being edited, this option is not available.  
  
-   **Save As** – Saves the tracking profile currently being edited to a name you specify. If no tracking profile is being edited, this option is not available.  
  
-   **Import BAM Activity Definition** – Imports an activity definition that has been applied. This menu item has the same functionality as the watermark link in the left frame, meaning the user can start this action from either place (the watermark being a kind of usability hint). This option is always available when there is a connection to the BizTalk Management database and BAM Primary Import database.  
  
-   **Exit** – Exits the TPE. Exiting during an active edit invokes a Save or Save As per Windows standards. This option is always available.  
  
### New Profile  
 The **New Profile** menu option opens a blank tracking profile source file with no contents against an empty BTT file (a tracking profile file). The default name of the new profile is TrackingProfile1 (…2, 3, etc.).  
  
> [!NOTE]
>  By default, the BizTalk Management database is set to the default BizTalk Management database of the BizTalk group. To change the management database, use the **Set Mgmt DB** option on the **Tools**. The BizTalk Management database setting is retained between sessions.  
  
### Open  
 The **Open** menu option allows the user to locate and select a single profile with which to work. Profiles are dependent on the assemblies they were created against being available in order to render and validate the profile.  
  
 If the original deployed assembly is no longer available or you need to change the assembly with which the profile is associated, you have the option of explicitly invoking the **Set Mgmt DB** action to refresh this link. You can also edit the profile and apply it.  
  
### Save  
 The **Save** option saves the tracking profile currently being edited. The first time Save is selected on new a tracking profile the option invokes the **Save As** dialog.  
  
### Save As  
 The **Save As** option allows you to specify the folder and the name for the tracking profile. The default extension for the tracking profile file is .btt.  
  
### Import BAM Activity Definition  
 The **Import BAM Activity Definition** option opens the Import BAM Activity Definition dialog box which is populated with a list of BAM activity definitions found in the BAM Primary Import database.  
  
 This feature is also invoked by clicking **Click here to import a BAM Activity Definition link** in the Activity View of a new tracking profile.  
  
 **Retrieve Existing Profile Check box**  
  
 This check box allows you to extract and include existing tracking profile mappings for the activity definition.  The check box is not selected by default.  
  
> [!NOTE]
>  When BAM activity definitions are imported with their tracking settings, existing mappings are validated against the assemblies, orchestrations, schemas, and ports in the currently selected BizTalk Management database. If the mappings are invalid with respect to the database, an error icon appears next to the invalid mapping. Instances where this could occur are a tracking profile that was deployed before an assembly was undeployed, or where the BAM Primary Import database is being shared by multiple groups and multiple BizTalk Management databases. In the latter case, the error icons appear if the tracking profile was deployed from one group and imported from another group.  
  
### Exit  
 The **Exit** Option closes the TPE. If there has been a modification to the tracking profile you are prompted to save the profile when the Tracking Profile Editor closes.  
  
## Tools Menu  
 The Tools menu contains the following options:  
  
-   **Apply Tracking Profile** – Stores the profile in the BAM Primary Import database.  
  
-   **Remove Tracking Profile** – Removes the tracking profile mappings from the BAM Primary Import database.  
  
-   **Set Management Database** – Sets the management database that the TPE is working against.  
  
-   **Options** – Allows you to set TPE options.  
  
### Apply Tracking Profile  
 The **Apply Tracking Profile** menu option stores the tracking profile mapping to the specified assembly as well as to the corresponding orchestrations and ports. All the artifacts that are referred to in the tracking profile should be available in a specified BizTalk Management database. All new instances of the relevant services use the new tracking profile when starting.  
  
 You can work against multiple assemblies at the same time. You do not work with the assemblies concurrently, but multiple assemblies can be accessed in a single editing session relative to any single BAM activity definition.  In other words, if you import a BAM activity definition and then select three assemblies from which to draw tracked items, the profile that TPE creates is applied to multiple profiles that are associated with the orchestrations and ports that are used in the tracking profile. The tracking profile always contains information about all assemblies associated with any given BAM activity definition.  
  
> [!CAUTION]
>  In BizTalk Server, each BAM activity can only have one tracking profile deployed against it. In other words, if you deploy a profile that has an activity mapped to an orchestration and later deploy a different profile that has the same activity mapped to a different orchestration, the first profile deployed is over written.  
  
### Remove Tracking Profile  
 The **Remove Tracking Profile** menu option removes the tracking profile for the loaded activity definition and its corresponding orchestrations and ports. You are prompted for confirmation before this action is completed.  
  
### Set Management Database  
 The **Set Management Database** menu option specifies the BizTalk Management database from which mapping sources can be chosen, and through which BAM activity definitions are found. By default, the tracking profile is set to the default BizTalk Management database specified during configuration.  
  
 SQL connection strings can be specified in one of two manners:  
  
-   You can specify just the server name, and the TPE will connect to the default port.  
  
-   You can specify a server name and port pair, ServerName,port number. The TPE will connect to the computer running SQL Server that is using the specified port.  
  
## Help Menu  
 The Help menu contains the following options:  
  
-   **BizTalk Server Help** – Opens the BizTalk Server Help file.  
  
-   **Tracking Profile Editor Help** – Opens the TPE section in the BizTalk Server Help file.  
  
-   **BizTalk Server Online** - Opens BizTalk Server Online Help.  
  
-   **About Tracking Profile Editor** – Displays the standard About information.  
  
## See Also  
 [Components of the TPE](../core/components-of-the-tpe.md)   
 [Tracking Profile Editor](../core/tracking-profile-editor.md)