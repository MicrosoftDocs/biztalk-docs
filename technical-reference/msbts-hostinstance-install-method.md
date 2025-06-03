---
description: "Learn more about: MSBTS_HostInstance.Install Method"
title: MSBTS_HostInstance.Install Method
TOCTitle: MSBTS_HostInstance.Install Method
ms:assetid: 5859491c-44fb-4cee-945f-a0ef53be1866
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560275(v=BTS.80)
ms:contentKeyID: 51528191
ms.date: 12/06/2023
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_HostInstance.Install Method

 

Installs a service for the given instance of the BizTalk host.

## Method Declaration

*The syntax shown is language neutral.*

```C#
uint32 Install(string Logon, string Password, boolean GrantLogOnAsService, boolean IsGmsaAccount);  
```

## Parameters

*Logon*  
String containing the logon information used by the host instance.

*Password*  
String containing the password for the host.

*GrantLogOnAsService*  
Boolean determining whether the 'Log On As Service' privilege should be automatically granted to the specified logon user or not. This flag only has effect when the [HostType](msbts-hostinstance-hosttype-property-wmi.md) property is set to In-process.

*IsGmsaAccount*  
Boolean determining whether the logon account is a Group Managed Service Account.  If true, the password can be empty.  This parameter is only available for BizTalk 2020 and above.

> [!NOTE]
>
> Starting with BizTalk Server 2020 CU5, the `IsGmsaAccount` parameter is optional.

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

For samples illustrating the **MSBTS\_HostInstance** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

