---
title: "Common WIP and HIP Nodes | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3e1caac-8ce1-40ec-a42a-61c19969080a
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Common WIP and HIP Nodes
The following nodes are common to both Host-Initiated Processing and Windows-Initiated Processing.

## **AppFabric Cache Location**

If a configuration from a AppFabric Cache is desired, the cache information is specified here. The following three items appear in the right pane when the AppFabric Cache Location node is highted:

- **Cache Name**. The name of the AppFabric Cache.

- **Key**. An identifier that defines the cached configuration information.

- **Region**. An identifier that defines where in the cache the configuration object resides.

## **Configuration Read Order**

This setting indicates if the config file configuration will be used or if the configuration from an AppFabric Cache is preferred.  In the right pane the following two items appear:

- **App Config**.  Select First, Second or Unused.

- **Cache**.  Select First, Second or Unused.

   [!NOTE] The TI Runtime will use these entries to determine the order for reading in the configuration. To prevent the TI Runtime from attempting to use one of the options, select Unused.
   
## **Conversion Behavior**

The conversion behaviors affect how data conversion is done by the TI Runtime. Many of these replace registry entries from the older versions of Host Integration Server.  The values for each of these is True or False, the default value when creating a new config file is False.
- **Accept Bad COMP3 Sign**. The TI Runtime will ignore a bad sign value for a COMP-3 data value.

- **Accept Null Packed**. The TI Runtime will accept all null values for a packed decimal (COMP-3) data value.
- **Accept Null Zoned**. The TI Runtime will accept all null values for a zoned decimal (DISPLAY) data value.
- **Always Check for Null**. The TI Runtime will onways check for a null on a Windows string when sending a string to the host.
- **Strings are Null Terminated and Space Padded**. The TI Runtime will terminate a string when it encounters a null value and will pad a string with spaces when sending a string to the host.
- **Trim Trailing Nulls**. The TI Runtime will remove trailing nulls when sending a string to the host.
- **Convert Received Strings As Is**. The TI Runtime will ignore Null termination and space padding settings during unpack operations.
- **Allow null for Simple Redefines**. The TI Runtime will accept null values for Simple REDEFINE statements when sending and receiving data.
  ## Related Sections
  [Configuration for WIP](../core/configuration-for-wip.md)
 
  [Configuration for HIP](../core/configuration-for-hip.md)