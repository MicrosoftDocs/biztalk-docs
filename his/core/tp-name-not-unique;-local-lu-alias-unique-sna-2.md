---
description: "Learn more about: TP Name Not Unique; Local LU Alias Unique (SNA)"
title: "TP Name Not Unique; Local LU Alias Unique (SNA)2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# TP Name Not Unique; Local LU Alias Unique (SNA)
Another way to specify the intended system where the invokable TP will run is to give the same name to multiple invokable TPs, but associate each TP with a unique local LU alias. To do this, configure each invokable TP (through registry or environment variables) to use a unique local LU alias. Then set up the invoking TPs so that each one is routed not only to the correct TP name but also to the correct partner LU alias for the intended invokable TP.
