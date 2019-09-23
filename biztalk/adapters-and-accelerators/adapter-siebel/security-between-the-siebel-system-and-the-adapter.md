---
title: "Security between the Siebel system and the adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "security, IPsec"
  - "connection URI"
  - "security considerations, between the Siebel system and the adapter"
ms.assetid: 40b03d4e-f489-4dce-ba7b-6b6f394275ac
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Security between the Siebel system and the adapter
## Encryption and authentication
The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] can support rsa or mscrypto encryption on the data that it exchanges with the Siebel system. You configure the encryption mode through a query string parameter in the connection URI. For more information about the Siebel connection URI, see [Create The Siebel System Connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md). For more information about rsa and mscrypto encryption support by Siebel, see the Siebel documentation.

 Specifying an encryption mode can help to ensure privacy of data exchanged between the adapter and the Siebel system; however, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] does not provide mechanisms that support authorization, authentication or data integrity on such exchanges. If these issues are a concern in your environment, you must provide a security mechanism to help mitigate them.

 One possible mechanism for helping to provide more security across the network is Internet Protocol Security (IPsec). IPsec is a framework of open standards for protecting communications over Internet Protocol (IP) networks. For more information about IPsec and about using IPsec with Microsoft products, see the Microsoft TechNet article "IPsec" at [http://go.microsoft.com/fwlink/?LinkID=196851](https://go.microsoft.com/fwlink/?LinkID=196851).

 The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] supports authorization and authentication on the connections that it establishes with the Siebel system through user name password credentials that you supply. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] uses these credentials to authenticate the user on the Siebel system when it opens a connection. These credentials provide a level of authorization on the Siebel system for the connection. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] provides a number of methods through which you can supply these credentials. For information about how to more securely provide Siebel credentials in BizTalk solutions, see [Security with Siebel adapter and BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md). For information about how to more securely provide Siebel system credentials in programming solutions, see [Secure programming with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/secure-programming-with-the-siebel-adapter.md).

> [!NOTE]
>  The credentials used by the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to establish a connection to the Siebel system do not provide message-level or transport-level authentication or authorization for data traveling across the network. They are only used to open a connection and authenticate the user on the Siebel system.

## See Also
[Secure your Siebel applications](../../adapters-and-accelerators/adapter-siebel/secure-your-siebel-applications.md)