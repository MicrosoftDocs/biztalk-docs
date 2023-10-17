---
description: "Learn more about: Values for lua_message_type"
title: "Values for lua_message_type2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b2b8db2-4f12-432b-a926-e6c465733e68
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Values for lua_message_type
The following table describes the possible values for **lua_message_type**.  
  
|Message type|SNA data|SLI_SEND|SLI_BID<br /><br /> SLI_RECEIVE|RUI_BID<br /><br /> RUI_READ|  
|------------------|--------------|---------------|-------------------------------|----------------------------|  
|0xC8|BID|X|X|X|  
|0x31|BIND||Extension*|X|  
|0x70|BIS|X|X|X|  
|0x83|CANCEL|X|X|X|  
|0x84|CHASE|X|X|X|  
|0xA1|CLEAR|||X|  
|0xD0|CRV|||X|  
|0x01|LU_DATA**|X|X|X|  
|0x04|LUSTAT_LU**|X|X|X|  
|0x14|LUSTAT_SSCP**|X|X|X|  
|0x81|QC|X|X|X|  
|0x80|QEC|X|X|X|  
|0x82|RELQ|X|X|X|  
|0xA3|RQR|X||X|  
|0x02|RSP|X|X||  
|0x05|RTR|X|X|X|  
|0x71|SBI|X|X|X|  
|0xC0|SHUTD|||X|  
|0xC9|SIGNAL|X|X|X|  
|0xA0|SDT|||X|  
|0x11|SSCP_DATA**|X|X|X|  
|0xA2|STSN||Extension*|X|  
|0x32|UNBIND|||X|  
  
 *The SLI receives and responds to the BIND, CRV, and STSN requests through the LUA  interface extension routines.  
  
 **Not an SNA command.
