---
title: "Matching Invoking and Invokable TPs (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c82b86fe-b7a0-402b-a2e6-74b4827f017b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Matching Invoking and Invokable TPs (CPI-C)
Each  SNA service maintains a list of available invokable transaction program (TP) names and any logical unit (LU) aliases to be associated with the TP names. This information is obtained as follows:  
  
- For autostarted invokable TPs, registry or environment variables identify a TP name containing a maximum of eight characters, and can specify an associated LU. This information is sent from the client to the server that sponsors the client. A client learns about the domain through a sponsor connection to a server. Clients must establish the sponsor connection before proceeding with any other tasks.  
  
- For operator-started invokable TPs, a TP name (with a maximum of 64 characters) is specified in [Specify_Local_TP_Name](./specify-local-tp-name-cpi-c-2.md). The TP name is truncated to eight characters and sent from the client to the server that sponsors the client, along with the alias of an associated LU if one has been configured through a registry or environment variable.  
  
  > [!NOTE]
  >  If you want a TP name to be unique, it is recommended that you limit the name to eight characters or fewer, or make the name unique within the first eight characters. This is because the preliminary routing of allocation requests is carried out using the first eight characters. Although further matching is later carried out between the full TP names, it is inefficient to allow the preliminary routing to succeed when in some cases the later matching will fail.  
  
  The next step in the matching of invoking and invokable TPs is the creation of a side information table from the parameters in the symbolic destination name. Then the invoking TP issues the [Allocate](./allocate-cpi-c-2.md) call and an allocation request flows to the partner LU specified in the side information table, stating the name of the invokable TP that has been requested (also listed in the side information table).  
  
  When an allocation request arrives, the SNA service compares the requested invokable TP name and LU alias to the list of available invokable TPs (which can include associated LU aliases). The comparison can be modified by registry variables, but by default is carried out as follows:  
  
- Although the TP name requested in the symbolic destination name can be as long as 64 characters, any name received through a registry or environment variable is limited to eight characters or less. Therefore, only the first eight characters of TP names are used in comparisons.  
  
- The comparison is carried out first on both the TP name and the LU alias. An invokable TP for which there is a match on both TP name and LU alias will be chosen ahead of a TP for which no LU alias has been configured through a registry or environment variable. A TP for which no LU alias has been configured can be matched with any request that specifies that TP name, because there cannot be a mismatch based on LU alias.  
  
- The comparison of requested and available TP names is carried out in a specific order:  
  
  1.  The SNA service first checks for operator-started invokable TPs on the local system (the local Host Integration Server).  
  
  2.  If no match is found, the SNA service checks for autostarted invokable TPs on the local system (the local Host Integration Server).  
  
  3.  If no match is found, the SNA service checks for operator-started invokable TPs on other computers running Host Integration Server or clients.  
  
  4.  If no match is found, the SNA service checks for autostarted invokable TPs on other computers running Host Integration Server or clients.  
  
  This comparison can be modified somewhat by registry entries for the SnaServr service. The entries are called **DloadMatchTPOnly** and **DloadMatchLocalFirst**.  
  
  If a match is found, the SNA service signals the system containing the requested TP to connect to that SNA service. If no match is found, the SNA service rejects the incoming request.  
  
  For suggestions about specific ways to handle TP names and LU aliases, see [Arranging TPs Within an SNA Network](../core/arranging-tps-within-an-sna-network-cpi-c-2.md).  
  
> [!NOTE]
>  Because of the way Common Programming Interface for Communications (CPI-C) works, an allocation request does not flow until local data buffers are full, or a [Confirm](./confirm-cpi-c-2.md) or [Flush](./flush-cpi-c-2.md) call is made. This may mean that the allocation request does not flow until some time after the [Allocate](./allocate-cpi-c-2.md) call is made. Therefore, any allocation failure caused by the rejection of the allocation request at the partner LU will be observed as the failure of a later call with one of the allocation failure return codes.