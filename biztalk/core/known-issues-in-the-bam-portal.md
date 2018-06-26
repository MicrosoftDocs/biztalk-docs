---
title: "Known Issues with BAM Portal | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e681e910-c664-479c-86f3-a6ae0ec97775
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues in the BAM Portal
This topic contains information to help you identify and resolve issues that can occur while you are using the BAM portal.  
  
## Errors occur when the BAM Portal and IE are on the same computer, and Security Settings are Low  
 **Problem**  
  
 When using Internet Explorer, you may encounter the error message **Server Error in '/BAM' Application** under the following circumstances:  
  
- While clicking a related activity that points to a non-existing activity instance.  
  
- While clicking the **Save Alert** button in the following scenario:  
  
  -   You create a query on the **ActivitySearch** page and then click **Set Alert**.  
  
  -   You complete the alert fields and then click **Save Alert**.  
  
  -   You click the back button.  
  
  -   You click the **Save Alert** button again.  
  
  **Cause**  
  
  When running Internet Explorer with the security level set to low, Web requests are executed with low privileges. To fulfill the Windows integrated security challenge, Internet Explorer passes a user token with low privileges.  
  
  If you are using Internet Explorer on the same computer as the one on which the BAM portal is installed, and you set the security level in Internet Explorer to low, the portal impersonates the user with the low privileges token. This token does not have the permissions to write to the event log. If the portal encounters an error, it attempts to log it to the event log and will fail since the reduced privileges of the user token are not sufficient to access the event log.  
  
  **Resolution**  
  
  If you need to browse from the local computer, you should add http://localhost to the list of trusted sites.  
  
#### Add localhost to the list of trusted sites  
  
1.  In Internet Explorer, click **Tools**, and then click **Internet Options**.  
  
2.  Click the **Security** tab, and then click **Trusted Sites** in the **Select a zone to view or change security settings** window.  
  
3.  Click the **Sites** button.  
  
4.  In the **Add this website to the zone** text box, type **http://localhost**. If the **Require server verification (https:) for all sites in this zone** check box is selected, clear it and then click the **Add** button. The site, http://localhost, will appear in the **Websites** list.  
  
5.  If necessary, restore the **Require server verification (https:) for all sites in this zone** check box to its original state.  
  
6.  Click the **Close** button, and then click **OK**.  
  
## Bam Portal Aggregations Do Not Populate Existing Data When Using an IP Address as a URL in Internet Explorer
 **Problem**  
  
 When using an IP address as a URL with Internet Explorer to view the BAM portal, aggregations display the following message: "No detail. The query could not be processed."  
  
 **Cause**  
  
 The default security settings in Internet Explorer may prevent access to sites using IPv4 and IPv6 addresses as URLs.  
  
 **Resolution**  
  
 Add the site address to the trusted sites list and enable access to data sources across domains.  
  
#### Add the IP address to the trusted sites list  
  
1.  In Internet Explorer, click **Tools**, and then click **Internet Options**.  
  
2.  Click the **Security** tab, and then click the **Trusted sites** security zone.  
  
3.  Click the **Sites** button.  
  
4.  In **Add this website to the zone**, type the IP address of the BAM portal, and then click **Add**.  
  
5.  Click **Close**, and then click **OK**.  
  
#### Enable access to data sources across domains  
  
1.  In Internet Explorer, click **Tools**, and then click **Internet Options**.  
  
2.  Click the **Security** tab, and then click the **Trusted Sites** security zone.  
  
3.  Click the **Custom Level** button as you scroll down to the **Miscellaneous** node of the **Settings** tree.  
  
4.  In the **Access data sources across domains** node, click the **Enable radio** button, and then click **OK**.  
  
## BM.exe does not run in PowerShell  
 **Problem**  
  
 The following command throws an error when run in PowerShell.  
  
```  
bm.exe get-config -FileName:config.xml  
```  
  
 **Cause**  
  
 PowerShell could not locate the path of .exe and config files.  
  
 **Resolution**  
  
 If you use bm.exe in PowerShell, specify the full path of .exe and config files. For example: `bm.exe get-config -FileName:config.xml` should be specified as `“%BizTalkPathTracking%”\bm.exe get-config -FileName:”%InstallDir%”\Tracking\config.xml`.  
  
## See Also  
 [Planning for the BAM Portal](../core/planning-for-the-bam-portal.md)