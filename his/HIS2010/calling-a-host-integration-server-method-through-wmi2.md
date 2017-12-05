---
title: "Calling a Host Integration Server Method through WMI2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d06cf84-4c5f-436d-adca-ef20030159a3
caps.latest.revision: 3
---
# Calling a Host Integration Server Method through WMI
You have two options when calling methods through WMI: you may call a WMI method, or a provider method. A WMI method is supported by the WMI infrastructure, and provides general services such as query support or log on access. For example, [Logging on to Host Integration Server Through a WMI Provider](../HIS2010/logging-on-to-host-integration-server-through-a-wmi-provider1.md) and [Accessing a Host Integration Server Property through WMI](../HIS2010/accessing-a-host-integration-server-property-through-wmi1.md) describe calling the **GetObject** and **ExecQuery** WMI methods. In contrast, a provider method is supported by the provider, and is unique to each service. Most HIS provider methods deal with controlling services. For example, the **WmiSna** provider supports the **MsSna_ServiceSNA** class, which in turn supports the **Start**, **Stop**, **Pause**, and **Resume** methods. The actual process of calling a WMI method or a provider method is the same as calling any other COM or scripting interface.