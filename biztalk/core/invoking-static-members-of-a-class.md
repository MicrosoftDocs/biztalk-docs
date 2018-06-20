---
title: "Invoking Static Members of a Class | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a51171c-8de0-45dd-8659-f674cf27acbe
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invoking Static Members of a Class
By default, the rule engine requires you to assert an instance of a .NET class to execute a policy that invokes a static member of the .NET class. You can modify this behavior by changing the value of the **StaticSupport** registry key under **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0** to one of the values in the following table.  
  
|StaticSupport registry value|Rule engine behavior|  
|----------------------------------|--------------------------|  
|0|Default value. The rule engine follows the BizTalk Server 2004 model, where the static method is called only when an instance of the .NET class is asserted.|  
|1|An object instance is not required. The static method is called when the rule is evaluated or executed.|  
|2|An object instance is not required. The static method is called at the policy translation time if all parameters are constant. This is a performance optimization because the static method is called only once even though it is used in multiple rules in conditions. Note that static methods used as actions will not be executed at the translation time, but static methods used as parameters may be executed.|  
  
## Adding and Changing the StaticSupport Registry Key  
 If you do not see the **StaticSupport** registry key under **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**, you should add it by performing the following steps.  
  
 **To add the StaticSupport registry key**  
  
1. Click **Start**, click **Run**, type **RegEdit**, and then click **OK**.  
  
2. Expand **HKEY_LOCAL_MACHINE**, expand **Software**, expand **Microsoft**, expand **BusinessRules**, and then select **3.0**.  
  
3. In the right pane, right-click, point to **New**, and then click **DWORD value**.  
  
4. For **Name**, type **StaticSupport**.  
  
   If the **StaticSupport** registry key already exists, and you need to change its value, perform the following steps.  
  
> [!IMPORTANT]
>  If BizTalk is installed on a 64-bit machine, then you can add **StaticSupport** registry key using either of the following options:  
> 
> - You need to look under HKLM\Software\Wow6432Node\Microsoft\BusinessRules\3.0. If this key exists, then you can add **StaticSupport** here.  
>   -   Another option is to put **StaticSupport** in the **BTNTsvc[64].exe.config** file, as any settings here override what's in the Registry.  Further, one can also make the argument that this option is preferred since it isolates the change in default behavior to BizTalk only, whereas Registry settings are global to the Operating System.  
  
 **To change the value of the StaticSupport registry key**  
  
1.  Click **Start**, click **Run**, type **RegEdit**, and then click **OK**.  
  
2.  Expand **HKEY_LOCAL_MACHINE**, expand **Software**, expand **Microsoft**, expand **BusinessRules**, and then expand **3.0**.  
  
3.  Double-click the **StaticSupport** registry key, or right-click it and then click **Modify**.