---
description: "Learn more about: Alert Subscription Management Commands"
title: "Alert Subscription Management Commands"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Alert Subscription Management Commands
The BAM management utility subscription management commands allow you to work with alert subscriptions.  
  
-   get-subscription: Gets a list of subscribers to an alert.  
  
-   add-subscription: Adds a subscriber to an alert.  
  
-   remove-subscription: Removes a subscriber from an alert.  
  
> [!NOTE]
>  You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch. Using the Trace switch overrides the tracing settings in the configuration file. The switch can be used in conjunction with any normal BM command.  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## get-subscription Command  
 **Usage**  
  
 **bm.exe get-subscriptions -View:\<view name\> -Alert:\<alert name\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|View:\<view name\>|The name of the view on which the alert is to be specified.|  
|Alert:\<alert name\>|The name of the alert from which to get the subscription.|  
|Server:\<server\>|Optional: The name of the server on which the view resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the view resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Lists all the subscribers to the specified alert.  
  
 **Examples**  
  
```  
bm.exe get-subscriptions -View:SalesManagerView -Alert:SalesTooLow  
bm.exe get-subscriptions -View:Shipments -Alert:SlowShipment -Server:Ship1  
```  
  
## add-subscription Command  
 **Usage**  
  
 **bm.exe add-subscription -View:\<view name\> -Alert:\<alert name\> -AccountName:\<account name\> -Type: [ File &#124; Email ][ -Email:\<e-mail address\> ][ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|View:\<view name\>|The name of the view on which the alert is specified.|  
|Alert:\<alert name\>|The name of the alert to which to subscribe.|  
|AccountName:\<account name\>|The account, in domain\user format, to subscribe to the alert.|  
|Type: [ File &#124; Email ]|The delivery type of the alert. If you specify a delivery type of e-mail, you must include the e-mail parameter on the command line.|  
|Email:\<e-mail address\>|Optional: The email address to which the alert notification will be delivered.|  
|Server:\<server\>|Optional: The name of the server on which the view resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the view resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Adds a subscription for the specified account to the specified alert.  
  
 **Examples**  
  
```  
bm.exe add-subscription -View:v1 -Alert:a2 -AccountName:domain\user -Type:File  
bm.exe add-subscription -View:v1 -Alert:a2 -AccountName:domain\user -Type:Email -Email:useremail@domain.com  
```  
  
## remove-subscription Command  
 **Usage**  
  
 **bm.exe remove-subscription -View:\<view name\> -Alert:\<alert name\> -AccountName:\<account name\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|View:\<view name\>|The name of the view on which the alert is specified.|  
|Alert:\<alert name\>|The name of the alert.|  
|AccountName:\<account name\>|The account, in domain\user format, to remove from the alert.|  
|Server:\<server\>|Optional: The name of the server on which the view resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the view resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Removes the subscription of the specified account from the specified alert. All subscriptions for the specified account are removed.  
  
 **Examples**  
  
```  
bm.exe remove-subscription -View:v1 -Alert:a2 -AccountName:domain\user  
bm.exe remove-subscription -View:v1 -Alert:a2 -AccountName:user -Server:s1  
```  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)
