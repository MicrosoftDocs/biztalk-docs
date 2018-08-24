---
title: BizTalk GroupNode
TOCTitle: BizTalk GroupNode
ms:assetid: 2d4c607f-af04-4c39-bbbf-ba364be2d3dd
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559395(v=BTS.80)
ms:contentKeyID: 51527016
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.node.group
---

# BizTalk GroupNode

 

Use the **BizTalk Group \[\<Group Name\>\]** node to view and manage the BizTalk Server implementation. Right-click the **BizTalk Group \[\<Group Name\>\]** node to display the following commands:

1.  **Remove**. Removes the Group from the Administration console view. Removing the group does not remove the databases, and the user may reconnect to the group at any time.

2.  **Settings**. Displays the BizTalk Settings Dashboard wizard. For more information, refer [BizTalk Settings Dashboard UI Help](biztalk-settings-dashboard-ui-help.md)

3.  **Refresh**. Updates the details pane with the latest group configuration and status information.

4.  **Properties**. Displays the **Group Properties: BizTalk Group Properties** window.

Click **BizTalk Group \[\<Group Name\>\]** node to view Group Overview on the details pane, containing the following tabs:

  - **Group Hub**. This menu item displays the Configration Overview providing information about Group name, Server and Database.

  - **New Query**. This menu item displays a submenu containing the following commands. If the **Group Hub** tab is selected in the details pane, only **New Query** and **Close All** are visible on the submenu. When a query tab is selected in the details pane, the entire submenu appears.
    
      - **New Query**. Displays a query form in the details pane. You can use the query form to find information in the BizTalk Message Box.
    
      - **Copy Query**. Creates a copy of the selected query.
    
      - **Rename**. Renames the selected query.
    
      - **Open**. Opens an existing BizTalk query (\*.btq) file.
    
      - **Close**. Closes the selected query.
    
      - **Close All**. Closes all queries in the details pane.
    
      - **Save As**. Saves the selected query to a location you specify.
    
      - **Run**. Runs the selected query.

## See Also

[BizTalk Groups](https://msdn.microsoft.com/en-us/library/aa559010\(v=bts.80\))  
[Managing Groups](https://msdn.microsoft.com/en-us/library/aa560678\(v=bts.80\))  
[How to Modify Group Properties](https://msdn.microsoft.com/en-us/library/aa560305\(v=bts.80\))  
[How to Remove a Server from a Group](https://msdn.microsoft.com/en-us/library/aa561173\(v=bts.80\))

