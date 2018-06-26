---
title: "Matching Invoking and Invokable TPs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e968af29-a458-431f-8005-71a2d102b1d0
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Matching Invoking and Invokable TPs
Each computer running Host Integration Server maintains a list of available invokable TP names and any LU aliases to be associated with the TP names. This information is obtained as follows:  
  
- For autostarted invokable TPs, registry or environment variables identify a TP name containing a maximum of eight characters, and can specify an associated LU. This information is sent from the client to the server that sponsors the client. A client learns about the domain through a sponsor connection to a server; clients must establish the sponsor connection before proceeding with any other tasks.  
  
- For operator-started invokable TPs, a TP name (with a maximum of 64 characters) is specified with the [RECEIVE_ALLOCATE](./receive-allocate1.md) verb. The TP name is truncated to eight characters and sent from the client to the server that sponsors the client, along with the alias of an associated LU if one has been configured through a registry or environment variable.  
  
  > [!NOTE]
  >  If you want a TP name to be unique, it is recommended that you limit the name to eight characters or fewer, or make the name unique within the first eight characters. This is because the preliminary routing of allocation requests is carried out using the first eight characters. Although further matching is later carried out between the full TP names specified in [ALLOCATE](./allocate2.md) or [MC_ALLOCATE](./mc-allocate2.md) and **RECEIVE_ALLOCATE**, it is inefficient to allow the preliminary routing to succeed when in some cases the later matching will fail.  
  
  The next step in the matching of invoking and invokable TPs is that the invoking TP issues the **ALLOCATE** or **MC_ALLOCATE** verb. After an invoking TP in a Host Integration Server domain successfully issues this verb, an allocation request flows to the partner LU specified in the **ALLOCATE** or **MC_ALLOCATE** verb, stating the name of the invokable TP that has been requested.  
  
  When an allocation request arrives, Host Integration Server compares the requested invokable TP name and LU alias to the list of available invokable TPs (which can include associated LU aliases). The comparison can be modified by registry variables, but by default is carried out as follows:  
  
- Although the TP name requested in the **ALLOCATE** or **MC_ALLOCATE** verb can be as long as 64 characters, any name received through a registry or environment variable is limited to eight characters or less. Therefore, only the first eight characters of TP names are used in comparisons.  
  
- The comparison is carried out first on both the TP name and the LU alias. An invokable TP for which there is a match on both TP name and LU alias will be chosen ahead of a TP for which no LU alias has been configured through a registry or environment variable. A TP for which no LU alias has been configured can be matched with any request that specifies that TP name, since there cannot be a mismatch based on LU alias.  
  
- The comparison of requested and available TP names is carried out in a specific order:  
  
  1.  Host Integration Server first checks for operator-started invokable TPs on the local system (the local computer running Host Integration Server).  
  
  2.  If no match is found, Host Integration Server checks for autostarted invokable TPs on the local system (the local computer running Host Integration Server).  
  
  3.  If no match is found, Host Integration Server checks for operator-started invokable TPs on other Host Integration Server clients or servers.  
  
  4.  If no match is found, Host Integration Server checks for autostarted invokable TPs on other Host Integration Server clients or servers.  
  
  This comparison can be modified somewhat by registry entries for the SnaServer service. The entries are called **DloadMatchTPOnly** and **DloadMatchLocalFirst**, and are described in the *Microsoft Host Integration Server Reference online book*.  
  
  If a match is found, Host Integration Server signals the system containing the requested TP to connect to that server running Host Integration Server. If no match is found, Host Integration Server rejects the incoming request.  
  
  For suggestions about specific ways to handle TP names and LU aliases, see [Arranging TPs Within an SNA Network](../core/arranging-tps-within-an-sna-network2.md).  
  
> [!NOTE]
>  Because of the way APPC works, an allocation request will not flow until local data buffers are full, or a confirm or flush verb is issued. This can mean that the allocation request does not flow until some time after the [ALLOCATE](./allocate2.md) or [MC_ALLOCATE](./mc-allocate2.md) verb is issued. Therefore, any allocation failure caused by the rejection of the allocation request at the partner LU will be observed as the failure of a later verb with one of the allocation failure return codes.