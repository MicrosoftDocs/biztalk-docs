---
description: "Learn more about: How to Change the Tracking QueryTimeout Value"
title: "How to Change the Tracking QueryTimeout Value"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Change the Tracking QueryTimeout Value
By default, message and service instance tracking will time out if a query runs longer than 60 seconds. You can change the timeout value in the registry to enable queries to run longer than 60 seconds.  
  
> [!CAUTION]
>  Incorrectly editing the registry may severely damage your system. Before making changes to the registry, you should back up any valued data on the computer.  
  
## Prerequisites  
 You must be logged on as a member of the Administrators group to perform this procedure.  
  
### To change the query timeout value  
  
1.  Click **Start**, click **Run**, type **regedit**, and then click **OK**.  
  
2.  In Registry Editor, locate and then click the following subkey:  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0**  
  
3.  If there is a Tracking subkey, go to step 6.  
  
4.  To create a Tracking subkey, on the **Edit** menu, point to **New**, and then click **Key**.  
  
5.  Type **Tracking**, and then press ENTER.  
  
6.  Locate and then click the following subkey:  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\Tracking**  
  
7.  On the **Edit** menu, point to **New**, and then click **DWORD Value**.  
  
8.  Type **ConnectionTimeout**, and then press ENTER.  
  
9. Right-click **ConnectionTimeout**, and then click **Modify**.  
  
10. In the **Edit DWORD Value** dialog box, click **Decimal**.  
  
11. In the **Value data** box, type the value in seconds that you want to set for the query timeout value, and then click **OK**.  
  
12. On the **File** menu, click **Exit**.  
  
    > [!NOTE]
    >  You may need to close and then reopen the BizTalk Server Administration Console in order for the new timeout value to take effect.  
  
## See Also  
 [Viewing Historical and Tracked Data](../core/viewing-historical-and-tracked-data.md)
