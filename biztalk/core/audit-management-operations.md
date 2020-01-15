---
title: "Audit management operations | Microsoft Docs"
description: How to Audit management operations in BizTalk Server, including using turning on auditing, and reviewing the logs and the log structure.
author: "pravagar"
ms.author: "pravagar"
manager: "dougeby"
ms.date: "01/13/2020"
ms.topic: conceptual
ms.prod: biztalk-server

# optional metadata

#ROBOTS:

ms.reviewer: 
ms.suite:
ms.tgt_pltfrm:
ms.assetid: 
ms.custom: "biztalk-2020"

---

# Enable and view audit logs of common management operations in BizTalk Server

## Overview

**Starting with BizTalk Server 2020 and newer**, administrators can configure BizTalk Server to generate audit trail for management operation on application artifacts, such as send ports, receive ports, receive locations, orchestrations, and resources. Auditing of suspend/resume/terminate operations on service instances is also possible.

## Configure auditing

Auditing isn't enabled by default. To enable auditing:

 1. Open **BizTalk Server Administration** console, right-click the **BizTalk Group**, and select **Settings**.

 2. Check **Audit management operations**.

 3. Set **Maximum number of audit entries** to desired number. By default, BizTalk stores **10000** most recent entries.

 4. Select **OK** to save your changes.

 5. Refresh **BizTalk Server Administration**, if you wish to do more management operation in same session.

    > [!div class="mx-imgBorder"]
    > ![Configure BizTalk Server audit management operations](../core/media/configure-audit.png)

## View audit logs

1. Be sure BizTalk Server [operational data service](configure-the-operational-data-feed-for-power-bi-with-biztalk-server.md) is configured.
2. In your browser, enter `http://localhost/BizTalkOperationalDataService/AuditLogs`.
3. To retrieve audit log entries between a date range, use `http://localhost/BizTalkOperationalDataService/AuditLogs?fromDate=2019-12-25T01:00:00&toDate=2020-01-10`. Supported date formats are: `yyyy-MM-dd` or `yyyy-MM-ddThh:mm:ss`.

## Audit log structure

An audit log has following information:

- **Id**: Id of type Guid, unique per entry.
- **BatchId**: Same for all audited operations performed in a single SQL transaction. Insightful in correlating user operations with lower level details
- **UserPrincipal**: User who performed the operation, for example, `jeffsmith@Fabricom.com`.
- **Machine**: Machine name from which operation was performed, for example, `machine1@contoso.com`.
- **ArtifactId**: Unique id of the artifact.
- **ParentArtifactId**: If an artifact is child of another artifact, then this field will have artifact id of the parent.
- **ArtifactType**: Type of artifact on which operation was performed, for example `SendPort, ReceivePort, Application etc`.
- **ArtifactName**: User configured name of the artifact, for example, `FTP send port`.
- **OperationName**: Action performed on the artifact, for example `Create`.

  The following table summarizes possible operations name on different artifacts:

  | Artifact type | Operation name|
  | --- | --- |
  | Ports | Create/Update/Delete |
  | Service Instances | Suspend/Resume/Terminate |
  | Application resources | Add/Update/Remove |
  | Binding file | Import|

- **Payload**: Contains information about what is changed in JSON structure, for example, `{"Description":"New description"}`.
- **CreatedDate**: Timestamp when the operation was performed.

When an artifact is created/updated, one or more audit entries are logged. For example, when a send port is created, 3 audit entries are logged. One each for send port, primary transport, and secondary transport respectively. All these entries have the same **BatchId**. Audit log entries for the primary and secondary transport can be correlated with a send port using the **ArtifactId** and **ParentArtifactId** values.

## Next steps

[Track and monitor the health of your BizTalk Server](monitoring-biztalk-server.md).
